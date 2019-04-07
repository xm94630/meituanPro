<template>
  <div class="page-register">
    <div class="myHead">
      我是头部哦
      <el-button type="primary" size="small">登录</el-button>
    </div>

    <section>
      <el-form
        :model="ruleForm"
        :rules="rules"
        ref="ruleForm"
        label-width="100px"
        class="demo-ruleForm"
      >
        <el-form-item label="昵称" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>

        <el-form-item label="邮箱验证" prop="email">
          <el-input v-model="ruleForm.email"></el-input>
          <el-button size="mini" round @click="sendMsg">发送验证码</el-button>
          <span class="status">{{statusMsg}}</span>
        </el-form-item>

        <el-form-item label="验证码" prop="code">
          <el-input v-model="ruleForm.code" maxlength='4'></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="pwd">
          <el-input v-model="ruleForm.pwd" type='password'></el-input>
        </el-form-item>
        <el-form-item label="确认密码" prop="cpwd">
          <el-input v-model="ruleForm.cpwd" type='password'></el-input>
        </el-form-item>

        <el-form-item>
          <el-button type="primary" @click="register">同意并注册</el-button>
          <div class="error">{{error}}</div>
        </el-form-item>

      </el-form>
    </section>
  </div>
</template>

<script>
export default {
  layout: "blank", //这里是配置所采用的模板的
  data() {
    return {
      statusMsg:'',
      error:'',
      ruleForm: {
        name: "",
        code: "",
        pwd: "",
        cpwd: "",
        email: "",
      },
      rules: {
        name: [
          { required: true, message: "请输入昵称", trigger: "blur" },
        ],
      }
    };
  },
  methods: {
    sendMsg(){

    },
    register(){

    },
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  }
};
</script>

<style>
.myHead {
  border-bottom: solid 1px #eee;
}
</style>
