# linux selenium 使用说明（ubuntu 18、centos 7）

1.下载 google-chrome

```python
https://www.google.cn/chrome/  # 在谷歌官网最下方的其他平台选择 .deb 或者 .rpm 安装包
```

2.安装 google-chrome

```
ubuntu：
sudo dpkg -i google-chrome-stable_current_amd64.deb

centos:
rpm -ivh google-chrome-stable_current_x86_64.rpm
```

3.下载解压 chrome webdriver

```python 
http://npm.taobao.org/mirrors/chromedriver/ # 选择与 google-chrome 版本相同的 chromedriver，下载好直接解压
```

4.安装 selenium

```python
pip install selenium
pip install selenium -i https://pypi.tuna.tsinghua.edu.cn/simple
# 或者
pip3 install selenium
pip3 install selenium -i https://pypi.tuna.tsinghua.edu.cn/simple
```

5.使用 selenium

```python
from selenium import webdriver
from selenium.webdriver import ChromeOptions

base_url = 'http://www.baidu.com'

option = ChromeOptions()
option.add_argument("--headless")  # 设置不打开浏览器页面
option.add_argument('--no-sandbox')  # 设置在root权限下运行
option.add_experimental_option('excludeSwitches', ['enable-automation'])  # 设置以开发者模式运行浏览器
driver = webdriver.Chrome(executable_path="chromedriver的绝对路径，或者以创建软链接直接使用 chromedriver", chrome_options=option)
driver.get(base_url)
```

6.可能遇到的问题

```
centos 使用 selenium 可能遇到以下问题：

缺少 libappindicator3.so.1
yum install libappindicator-gtk3

缺少 liberation-fonts
yum install liberation-fonts

```

