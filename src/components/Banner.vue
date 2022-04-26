<template>

    <div id="banner">
<!--        <el-carousel height="400px">-->
<!--            <el-carousel-item v-for="item in banner_list">-->
<!--                &lt;!&ndash;<img src="../assets/img/banner1.png" alt="">&ndash;&gt;-->
<!--                <router-link :to="item.link">-->
<!--                    <img :src="item.img" :alt="item.name">-->
<!--                </router-link>-->

<!--            </el-carousel-item>-->
<!--        </el-carousel>-->

        <el-carousel :interval="5000" arrow="always">
            <el-carousel-item v-for="item in banner_list">
<!--                <h3>{{item}}</h3>-->
<!--                <img src="../assets/img/banner1.png" alt="">-->
<!--                <img src="../assets/img/banner2.png" alt="">-->

<!--                冒号是用来渲染数据的-->
                <router-link :to="item.link">
                    <img :src="item.img" :alt="item.name">
                </router-link>

            </el-carousel-item>
        </el-carousel>

    </div>

</template>

<script>
    export default {
        name: "Banner",
        // data:function(){},
        data() {
            return {
                banner_list: []
            }
        },
        created() {
            //当banner组件一创建，就向后台发请求，拿回轮播图数据
            this.$axios.get(this.$settings.base_url + '/home/banner/').then(response => {
                console.log(response.data)
                this.banner_list=response.data
            }).catch(error => {
            })
        },

    }
</script>

<style scoped>
    .el-carousel__item {
        height: 400px;
        min-width: 1200px;
    }

    .el-carousel__item img {
        height: 400px;
        /*margin-left: 20px;*/
        margin-left: calc(50% - 1920px / 2);
    }
</style>