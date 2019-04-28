<template>
  <div class="all">
    <div class="content">
      <span class="el-tag el-tag--info el-tag--small"   v-for="item in arr" :key="item.id">
        <span class="el-select__tags-text">{{item.num}}</span>
        <i class="el-tag__close el-icon-close" @click="deleteClick"  :id="item.id" ></i>
      </span>
    </div>
    <el-button type="primary"  @click="addClick">新增</el-button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "blackUncle",
  data() {
    return {
      arr:[{id:0,num:11111},{id:1,num:22222},{id:2,num:33333}]
    };
  },
  mounted: function() {},
  methods: {
    // alert('11'/)
    deleteClick(e){
      let _e=e;
      let newArr=[];
      newArr=this.arr.filter((e,i)=>{
        return (i==_e.target.id)?false:true
      })
      this.arr=newArr;
    },
    addClick(){
      // /^\d{4}-\d{1,2}-\d{1,2}/,：^[0-9]*$ 
       this.$prompt('请输入编号', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          inputPattern:/^[0-9]*$/ ,
          inputErrorMessage: '编号格式不正确'
        }).then(({ value }) => {
          // var obj={id:this.arr.lenth,num:value};
          this.arr.push(obj)
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '取消输入'
          });       
        });
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content {
  -webkit-appearance: none;
  background-color: #fff;
  background-image: none;
  border-radius: 4px;
  border: 1px solid #dcdfe6;
  box-sizing: border-box;
  color: #606266;
  display: inline-block;
  font-size: inherit;
  height: 40px;
  line-height: 40px;
  outline: none;
  padding: 0 15px;
  transition: border-color 0.2s cubic-bezier(0.645, 0.045, 0.355, 1);
}
.el-select .el-tag {
    box-sizing: border-box;
    border-color: transparent;
    margin: 2px 2px 2px 6px;
    background-color: #f0f2f5;
}

.el-tag--small {
    height: 24px;
    padding: 0 8px;
    line-height: 22px;
}
.el-tag--info {
    background-color: rgba(144,147,153,.1);
    border-color: rgba(144,147,153,.2);
    color: #909399;
}
.el-tag {
    background-color: rgba(64,158,255,.1);
    display: inline-block;
    padding: 0 10px;
    margin:0 10px 0 0;
    height: 32px;
    line-height: 30px;
    font-size: 12px;
    color: #409eff;
    border-radius: 4px;
    box-sizing: border-box;
    border: 1px solid rgba(64,158,255,.2);
    white-space: nowrap;
}
</style>
