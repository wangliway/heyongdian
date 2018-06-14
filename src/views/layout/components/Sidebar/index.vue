<template>
  <el-scrollbar wrapClass="scrollbar-wrapper">
    <div class="logo">
      <img :src="logo" alt="logo">
    </div>
    <div class="company">
      <span class="company-title">国正药业</span>
      <h4 class="company-sub-title">安徽国正药业股份有限公司</h4>
    </div>
    <el-menu
      mode="vertical"
      :show-timeout="200"
      :default-active="$route.path"
      :collapse="isCollapse"
      background-color=""
      text-color="#bfcbd9"
      active-text-color="#409EFF"
      class="sidebar"
    >
      <sidebar-item :routes="routes" class="nav-group"></sidebar-item>
    </el-menu>
  </el-scrollbar>
</template>

<script>
  import {mapGetters} from 'vuex'
  import SidebarItem from './SidebarItem'
  import logo from '@/assets/images/logo2@2x.png'

  export default {
    components: {SidebarItem},
    data() {
      return {
        logo
      }
    },
    computed: {
      ...mapGetters([
        'sidebar'
      ]),
      routes() {
        return this.$router.options.routes
      },
      isCollapse() {
        return !this.sidebar.opened
      }
    }
  }
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
  .logo {
    width: 260px;
    height: 115px;
    padding: 35px 40px 0 40px;
    overflow: hidden;
  }
  .company{
    color:white;
    margin-top: 20px;
    text-align: center;
    .company-title{
      display: inline-block;
      height: 40px;
      line-height: 40px;
      border: 1px solid white;
      border-radius: 20px;
      font-size: 24px;
      text-align: center;
      width: 180px;
      //三角形下拉标准
      background-image: url(../../../../assets/images/dropdown.png);
      background-repeat: no-repeat;
      background-position: center right 10px;
    }
  }
  .nav-group{
      width: 200px;
      margin-left: 30px;
  }

</style>
