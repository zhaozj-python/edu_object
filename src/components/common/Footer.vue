<template>
    <div class="footer">
        <ul>
            <li v-for="(footer, index) in footer_list1" :key="index"><span><router-link :to="footer.link">{{footer.title}}</router-link></span>
            </li>
            <li v-for="(footer, index) in footer_list2" :key="index"><span><a
                :href="footer.link">{{footer.title}}</a></span></li>

        </ul>
    </div>
</template>

<script>
    export default {
        name: "Footer",
        data() {
            return {
                footer_list1: [],
                footer_list2: [],
            }
        },
        methods: {
            get_footer1() {
                this.$axios.get(this.$settings.HOST + "home/footer1/").then(response => {
                    this.footer_list1 = response.data;
                })
            },
            get_footer2() {
                this.$axios.get(this.$settings.HOST + "home/footer2/").then(response => {
                    this.footer_list2 = response.data;
                })
            },
        },
        created() {
            this.get_footer1();
            this.get_footer2();
        }
    }
</script>

<style scoped>
    .footer {
        width: 100%;
        height: 128px;
        background: #25292e;
        color: #fff;
    }

    .footer ul {
        margin: 0 auto 16px;
        padding-top: 38px;
        width: 810px;
    }

    .footer ul li {
        float: left;
        width: 112px;
        margin: 0 10px;
        text-align: center;
        font-size: 14px;
    }

    .footer ul::after {
        content: "";
        display: block;
        clear: both;
    }

    .footer p {
        text-align: center;
        font-size: 12px;
    }
</style>
