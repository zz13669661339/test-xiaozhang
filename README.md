# test-xiaozhang
zidonghuceshijiaoben
#---------------------------屏蔽系统错误输出
import pytest#导入测试用例判断对错框架
import requests#发起请求接口框架
#----------------------------- 1. 定义Fixture 前置+后置
@pytest.fixture(scope="function")#装饰固定工具（也叫夹具）每个测试用例，都跑一次前后置
def setup_and_teardown():#定义一个函数跑完代码后产生的数据，将垃圾清理掉
    print("执行用例前执行setup() method is called.")#打印提醒开始测试，准备工作前
    yield  #执行测试用例中
    print("执行用例后执行tearDown() method is called.")#打印提醒测试以结束后执行清理垃圾及关闭工作
#------------------------------ 2. 测试用例，传入Fixture
def test_login_user4(setup_and_teardown):  # 这是一条登录测试，要使用前后置
    # 测试代码
    username = "user1"#用户名
    password = "password1"#密码
    url = "http://111.229.154.240:8080/api/login"#自己的服务器新建接口；或公司给的接口
    payload = {
        "username": username,#比喻盒子，盒子=user1就输出user1
        "password": password#比喻盒子，盒子=password1就输出password1
    }
    response = requests.post(url, json=payload, timeout=10)#更上面requests一样发请求，最多等10秒
    assert response.status_code == 200#判断接口是不是返回成功，200表示成功
    print(username)#打印用户名
    print(password)#打印密码
#-----------------------------
def test_login_user5(setup_and_teardown): # 这是一条登录测试，要使用前后置
    # 测试代码
    username = "user2"#用户名
    password = "password2"#密码
    url = "http://111.229.154.240:8080/api/login"#自己的服务器新建接口；或公司给的接口
    payload = {
        "username": username,#比喻盒子，盒子=user1就输出user1
        "password": password
    }
    response = requests.post(url, json=payload, timeout=10)#更上面requests一样发请求，最多等10秒
    assert response.status_code == 200#判断接口是不是返回成功，200表示成功
    print(username)#打印用户名
    print(password)#打印密码
# -----------------------------
def test_login_user6(setup_and_teardown): # 这是一条登录测试，要使用前后置
    # 测试代码
    username = "user3"#用户名
    password = "password3"#密码
    url = "http://111.229.154.240:8080/api/login"#自己的服务器新建接口；或公司给的接口
    payload = {
        "username": username,#比喻盒子，盒子=user1就输出user1
        "password": password #比喻盒子，盒子=password1就输出password1
    }
    response = requests.post(url, json=payload, timeout=10)#更上面requests一样发请求，最多等10秒
    assert response.status_code == 200#判断接口是不是返回成功，200表示成功
    print(username)#打印用户名
    print(password)#打印密码
