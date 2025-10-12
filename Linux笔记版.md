<h2 id="Q7YAM">一。软件安装</h2>
<h3 id="f6kih"><font style="color:rgb(15, 17, 21);">1. apt (Ubuntu软件安装/Debian 的包管理器)</font></h3>
<h3 id="adc45117"><font style="color:rgb(15, 17, 21);">基本使用：</font></h3>


```plain
# 更新软件包列表
sudo apt update

# 升级所有已安装的软件包
sudo apt upgrade

# 安装新软件
sudo apt install 软件包名

# 卸载软件（保留配置文件）
sudo apt remove 软件包名

# 完全卸载软件（包括配置文件）
sudo apt purge 软件包名

# 搜索软件包
apt search 关键词

# 查看软件包信息
apt show 软件包名
```

<h3 id="6cc83314"><font style="color:rgb(15, 17, 21);">常用示例：</font></h3>


```plain
sudo apt update
sudo apt install vim
sudo apt remove firefox
```

<h3 id="KqI3D">笔记</h3>
sudo apt update



![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760268210611-c568f59e-7372-4a13-9bee-59e49473114d.png)是要有密码输入的

sudo apt upgrade

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760271563705-90f351a6-7a42-4225-a10a-358cd3da52ec.png)

<h2 id="ts30M"><font style="color:rgb(15, 17, 21);">2. </font>**<font style="color:rgb(15, 17, 21);">snap</font>**<font style="color:rgb(15, 17, 21);"> (跨Linux发行版的软件包)</font></h2>
<h3 id="xC8hr"><font style="color:rgb(15, 17, 21);">基本使用：</font></h3>


```plain
# 查找snap软件包
snap find 软件名

# 安装snap软件
sudo snap install 软件名

# 列出已安装的snap软件
snap list

# 更新snap软件
sudo snap refresh 软件名

# 更新所有snap软件
sudo snap refresh

# 卸载snap软件
sudo snap remove 软件名
```

<h3 id="mzSTe"><font style="color:rgb(15, 17, 21);">常用示例：</font></h3>


```plain
sudo snap install spotify
sudo snap install code --classic  # 经典模式（更多权限）
snap list
```

snap list表示

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760271633130-dd9c9b30-38d7-49df-9b59-1eb0239ea7f8.png)

<h3 id="Td4Ue">笔记</h3>
主要就是跟软件有关的功能，理解为软件的引用

---

<h3 id="STK1t"><font style="color:rgb(15, 17, 21);">3. 后台运行命令的方法</font></h3>
<h3 id="HaoJV"><font style="color:rgb(15, 17, 21);">方法1：在命令末尾加 </font>`<font style="color:rgb(15, 17, 21);">&</font>`（首选）</h3>


```plain
# 命令会在后台运行，可以继续使用终端
sudo apt update &
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760271763104-82a7f14c-c891-45fb-a201-5b8f4ed277f1.png)用ctrl+c关不了，但能继续使用终端

<h3 id="sEsp6"><font style="color:rgb(15, 17, 21);">方法2：使用</font><font style="color:rgb(15, 17, 21);"> </font>`<font style="color:rgb(15, 17, 21);">nohup</font>`<font style="color:rgb(15, 17, 21);">（关闭终端后继续运行）</font></h3>


```plain
# 输出会保存到 nohup.out 文件
nohup sudo apt upgrade &

# 或指定输出文件
nohup sudo apt upgrade > upgrade.log 2>&1 &
```

<h3 id="sDKqr"><font style="color:rgb(15, 17, 21);">方法3：使用</font><font style="color:rgb(15, 17, 21);"> </font>`<font style="color:rgb(15, 17, 21);">screen</font>`<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">或</font><font style="color:rgb(15, 17, 21);"> </font>`<font style="color:rgb(15, 17, 21);">tmux</font>`</h3>


```plain
# 安装 screen
sudo apt install screen

# 创建新的会话
screen -S update_session

# 在会话中运行命令
sudo apt update && sudo apt upgrade
ctrl+A+D隐藏会话，终端消失


# 重新连接会话
screen -r update_session
```

安装screen

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760271992728-26d72484-c056-477f-b8a9-bff5d9c79b47.png)

创建新的对话![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760272077923-f4083031-04b4-4d08-a14c-62c99caa210c.png)





---

<h3 id="yoslO"><font style="color:rgb(15, 17, 21);">4. 实用技巧</font></h3>
<h3 id="sBJgv"><font style="color:rgb(15, 17, 21);">查看后台任务：</font></h3>


```plain
jobs          # 查看当前终端的后台任务
ps aux | grep apt   # 查看apt相关进程
```

<h3 id="yfVKh"><font style="color:rgb(15, 17, 21);">将后台任务调到前台：</font></h3>


<font style="color:rgb(15, 17, 21);background-color:#FBDE28;">fg %1  </font><font style="color:rgb(15, 17, 21);">      # 将1号后台任务调到前台</font>

<font style="color:rgb(15, 17, 21);">（与前面后台运行搭配）</font>

<h3 id="osgPQ"><font style="color:rgb(15, 17, 21);">组合使用示例：</font></h3>




```plain
# 一次性更新系统和snap软件
sudo apt update && sudo apt upgrade -y && sudo snap refresh

# 在后台运行更新
nohup sudo apt update && sudo apt upgrade -y > update.log 2>&1 &

# 查看更新日志
tail -f update.log
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275128422-7ad9f0bc-3a5f-45a8-b010-a23fc912d4f1.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275436879-78ba48d2-f911-4ef9-978d-aff295e70f47.png)（太慢了，把一次性更新系统和snap软件关了）

---

<h3 id="D7TVU"><font style="color:rgb(15, 17, 21);">5. 重要提示</font></h3>
+ **<font style="color:rgb(15, 17, 21);background-color:#FBDE28;">sudo</font>**<font style="color:rgb(15, 17, 21);">：安装软件通常需要管理员权限(●'◡'●)</font>
+ **<font style="color:rgb(15, 17, 21);background-color:#FBDE28;">-y</font>**<font style="color:rgb(15, 17, 21);background-color:#FBDE28;"> 参数：</font><font style="color:rgb(15, 17, 21);">自动确认（在脚本中很有用）</font>
+ **<font style="color:rgb(15, 17, 21);">&&</font>**<font style="color:rgb(15, 17, 21);">：只有前一个命令成功才执行下一个</font>
+ **<font style="color:rgb(15, 17, 21);">> file 2>&1</font>**<font style="color:rgb(15, 17, 21);">：将标准输出和错误输出都重定向到文件</font>

好的！我来为您详细解释 Linux 文件管理的基本命令。

<h1 id="lWsVM">二。文件管理</h1>
<h2 id="HXRsx"><font style="color:rgb(15, 17, 21);">1. </font>**ls**<font style="color:rgb(15, 17, 21);"> - </font><font style="color:rgb(15, 17, 21);background-color:#FBDFEF;">列出</font><font style="color:rgb(15, 17, 21);">目录内容╰(*°▽°*)╯list</font></h2>
<h3 id="inqMd"><font style="color:rgb(15, 17, 21);">基本语法：</font></h3>
```bash
ls [选项] [目录/文件]
```

<h3 id="LZWpX"><font style="color:rgb(15, 17, 21);">常用选项：</font></h3>
```bash
ls          # 列出当前目录内容（不显示隐藏文件）
ls -l       # 详细列表格式（显示权限、大小、时间等）
ls -a       # 显示所有文件（包括隐藏文件，以.开头）
ls -la      # 详细列表+显示所有文件
ls -lh      # 人类可读的文件大小（KB, MB, GB）
ls -t       # 按修改时间排序
ls -r       # 反向排序
ls -R       # 递归显示子目录
```

1.

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275219729-4c523f09-34c3-4fa2-9efd-9d1d1ad273bd.png)

2.![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275521640-1538d06e-fe71-4075-9452-b2b9168fef7c.png)详细表格

3.![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275552349-11413396-68ad-4db4-a360-91f57b57da66.png)显示所有文件

4.![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275613430-6523c4a4-09e7-428c-8e0a-89af3f354a21.png)相当于2.3叠加



感觉2.4挺常用的

<h3 id="oOv2d"><font style="color:rgb(15, 17, 21);">实用示例：</font></h3>
```bash
ls                    # 查看当前目录
ls /home              # 查看指定目录
ls -la ~/Documents    # 详细查看文档目录
ls *.txt              # 只显示txt文件
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760275703906-3dbf2409-9805-49f5-8036-7fbfac54d8b9.png)

---

<h2 id="qtZUo"><font style="color:rgb(15, 17, 21);">2. </font>**cp**<font style="color:rgb(15, 17, 21);"> -</font><font style="color:rgb(15, 17, 21);background-color:#CEF5F7;"> 复制</font><font style="color:rgb(15, 17, 21);">文件和目录copy</font></h2>
<h3 id="kOBhg"><font style="color:rgb(15, 17, 21);">基本语法：</font></h3>
```bash
cp [选项] 源文件 目标文件
cp [选项] 源文件... 目标目录
```

<h3 id="okha9"><font style="color:rgb(15, 17, 21);">常用选项：</font></h3>
```bash
cp file1 file2        # 复制文件
cp -r dir1 dir2       # 递归复制目录
cp -i file1 file2     # 交互模式（覆盖前询问）
cp -v file1 file2     # 显示复制过程
cp -u file1 file2     # 只复制更新的文件
```

记住顺序，前面那个是被复制的和要被复制的

<h3 id="VzCgD"><font style="color:rgb(15, 17, 21);">实用示例：</font></h3>
```bash
cp document.txt document_backup.txt          # 复制文件
cp -r old_folder/ new_folder/                # 复制目录
cp *.jpg /home/user/Pictures/                # 复制所有jpg文件
cp -iv file1 file2 file3 destination/        # 安全复制多个文件
```

touch建立，cp复制，再ls检验

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760277053230-b52eb73c-5db6-4774-bf19-cff99c1d8e08.png)



<h2 id="frbZT"><font style="color:rgb(15, 17, 21);">3. </font>**mv**<font style="color:rgb(15, 17, 21);"> - </font><font style="color:rgb(15, 17, 21);background-color:#FBDE28;">移动</font><font style="color:rgb(15, 17, 21);">或重命名文件和目录move</font></h2>
<h3 id="LwjrU"><font style="color:rgb(15, 17, 21);">基本语法：</font></h3>
```bash
mv [选项] 源文件 目标文件
mv [选项] 源文件... 目标目录
```

<h3 id="uhGYJ"><font style="color:rgb(15, 17, 21);">常用选项：</font></h3>
```bash
mv file1 file2        # 重命名文件
mv file1 dir/         # 移动文件到目录
mv -i file1 file2     # 交互模式（覆盖前询问）
mv -v file1 file2     # 显示移动过程
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760277173170-fe58b9c0-f4cb-4677-ac29-c7d07451e24a.png)![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760277282525-4639ce2a-b74f-47c2-a26d-fafab8398042.png)empty—file的源文件没有了，被改成了file1

<h3 id="bPXQy"><font style="color:rgb(15, 17, 21);">实用示例：</font></h3>
```bash
mv oldname.txt newname.txt          # 重命名文件
mv file.txt Documents/              # 移动文件到目录
mv dir1/ dir2/                      # 移动/重命名目录
mv -i important.txt backup/         # 安全移动（询问覆盖）
```



<h2 id="vBOmg"><font style="color:rgb(15, 17, 21);">4. </font>**rm**<font style="color:rgb(15, 17, 21);"> - 删除文件和目录remove</font></h2>
<h3 id="MlJEe"><font style="background-color:#FBDE28;">⚠️</font><font style="color:rgb(15, 17, 21);background-color:#FBDE28;"> 警告：rm 命令删除的文件无法恢复</font><font style="color:rgb(15, 17, 21);">！</font></h3>
<h3 id="yU0wJ"><font style="color:rgb(15, 17, 21);">基本语法：</font></h3>
```bash
rm [选项] 文件...
```

<h3 id="Bq8vE"><font style="color:rgb(15, 17, 21);">常用选项：</font></h3>
```bash
rm file.txt           # 删除文件
rm -r directory/      # 递归删除目录
rm -f file.txt        # 强制删除（不询问）
rm -i file.txt        # 交互模式（删除前询问）
rm -v file.txt        # 显示删除过程
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760277349999-c09bb42d-7160-424f-ba83-9a83760ddc3a.png)file1没有了

attention🙀🙀：directory是目录

<h3 id="ITrtf"><font style="color:rgb(15, 17, 21);">实用示例：</font></h3>
```bash
rm temp.txt                      # 删除文件
rm -r old_directory/             # 删除目录
rm -i important_file.txt         # 安全删除（询问确认）
rm -rf node_modules/             # 强制删除目录（常用但危险！）
```

<h3 id="qykaf"><font style="color:rgb(15, 17, 21);">安全提示：</font></h3>
```bash
# 创建安全别名（添加到 ~/.bashrc）
alias rm='rm -i'      # 总是询问确认

# 使用 trash-cli 代替 rm（可恢复）
sudo apt install trash-cli
trash-put file.txt    # 移动到回收站这个稳妥一点
```

---

<h2 id="C3d5a"><font style="color:rgb(15, 17, 21);">5. </font>**touch**<font style="color:rgb(15, 17, 21);"> - </font><font style="color:rgb(15, 17, 21);background-color:#FBDFEF;">创建</font><font style="color:rgb(15, 17, 21);">空文件或</font><font style="color:rgb(15, 17, 21);background-color:#FBDFEF;">更新</font><font style="color:rgb(15, 17, 21);">文件时间</font></h2>
<h3 id="QECsA"><font style="color:rgb(15, 17, 21);">基本语法：</font></h3>
```bash
touch [选项] 文件...
```

<h3 id="EunY5"><font style="color:rgb(15, 17, 21);">常用选项：</font></h3>
```bash
touch file.txt        # 创建空文件（如不存在）或更新时间为当前时间
touch -a file.txt     # 只更新访问时间
touch -m file.txt     # 只更新修改时间
touch -t 时间 文件    # 指定时间（格式：YYYYMMDDhhmm.ss）
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760276563810-655679a5-d5aa-4579-ac42-bc7c5f41774a.png)

<h3 id="qAzL0"><font style="color:rgb(15, 17, 21);">实用示例：</font></h3>
```bash
touch newfile.txt                    # 创建新文件
touch file1.txt file2.txt file3.txt  # 创建多个文件
touch -t 202312251430.00 log.txt     # 设置特定时间
touch *.txt                         # 更新所有txt文件时间
```

---

<h2 id="YvcOA"><font style="color:rgb(15, 17, 21);">6. </font>**综合实战示例**</h2>
<h3 id="gL9p4"><font style="color:rgb(15, 17, 21);">场景：整理照片文件</font></h3>
```bash
# 1. 查看当前目录
ls -l

# 2. 创建整理目录
mkdir photos videos documents

# 3. 移动照片文件
mv *.jpg *.png photos/

# 4. 移动视频文件  
mv *.mp4 *.avi videos/

# 5. 备份重要文档
cp -r documents/ documents_backup/

# 6. 删除临时文件
rm -f temp*.txt

# 7. 查看整理结果
ls -la
```

<h3 id="fLGQ3"><font style="color:rgb(15, 17, 21);">场景：批量处理文件</font></h3>
```bash
# 创建测试文件
touch file{1..5}.txt

# 批量重命名
for i in file*.txt; do
    mv "$i" "backup_$i"
done

# 查看结果
ls -l backup_*
```

---

<h2 id="wQ6jd"><font style="color:rgb(15, 17, 21);">7. </font>**安全操作建议**</h2>
1. **使用 -i 选项**<font style="color:rgb(15, 17, 21);">：特别是 rm 和 cp 命令</font>
2. **先使用 ls 确认**<font style="color:rgb(15, 17, 21);">：操作前先查看文件</font>
3. **使用 Tab 补全**<font style="color:rgb(15, 17, 21);">：减少输入错误</font>
4. **重要文件先备份**<font style="color:rgb(15, 17, 21);">：特别是使用 rm -rf 前</font>

<h3 id="Gdhfr"><font style="color:rgb(15, 17, 21);">推荐的安全别名（添加到 ~/.bashrc）：</font></h3>
```bash
alias cp='cp -i'
alias mv='mv -i'
alias rm='rm -i'
```

<font style="color:rgb(15, 17, 21);"></font>

<h1 id="da25N"><font style="color:rgb(15, 17, 21);">三。权限管理</font><font style="color:rgb(15, 17, 21);">🎏</font></h1>
<h2 id="zbh4q">1. **理解文件权限位（通俗来讲就是你有没有各种权限）**</h2>
<h3 id="MOTij">使用 `ls -l` 查看权限：（感觉这个挺常用的）</h3>
```bash
ls -l filename
# 输出示例：-rwxr-xr-- 1 user group 1234 Dec 25 10:30 filename
```

执行这个时第一行就是权限位

<h3 id="hfeJC">权限位解释：</h3>
```plain
-rwxr-xr--
↑|||||||||
|↓↓↓|↓↓↓|↓↓↓
| owner | group | others
|
文件类型 (-=文件, d=目录, l=链接)
```

类型位   用户权限   组权限   其他用户权限  
↓        ↓↓↓      ↓↓↓      ↓↓↓  
d        r w x    r - x    r - -  
|        | | |    | | |    | | |  
|        | | |    | | |    | | 其他用户执行权限  
|        | | |    | | |    | 其他用户写权限  
|        | | |    | | |    其他用户读权限  
|        | | |    | | 组执行权限  
|        | | |    | 组写权限  
|        | | |    组读权限  
|        | | 用户执行权限  
|        | 用户写权限  
|        用户读权限  
文件类型

**权限字符含义：**

+ `r` = 读权限 (4)
+ `w` = 写权限 (2) 
+ `x` = 执行权限 (1)
+ `-` = 无权限 (0)

<h4 id="WEI1L"><font style="color:rgb(15, 17, 21);">（2. 文件类型位（第1位）</font></h4>
| <font style="color:rgb(15, 17, 21);">字符</font> | <font style="color:rgb(15, 17, 21);">含义</font> | <font style="color:rgb(15, 17, 21);">说明</font> |
| --- | --- | --- |
| `<font style="color:rgb(15, 17, 21);">-</font>` | <font style="color:rgb(15, 17, 21);">普通文件</font> | <font style="color:rgb(15, 17, 21);">文本文件、二进制文件、图片等</font> |
| `<font style="color:rgb(15, 17, 21);">d</font>` | <font style="color:rgb(15, 17, 21);">目录</font> | <font style="color:rgb(15, 17, 21);">文件夹</font> |
| `<font style="color:rgb(15, 17, 21);">l</font>` | <font style="color:rgb(15, 17, 21);">符号链接</font> | <font style="color:rgb(15, 17, 21);">快捷方式</font> |
| `<font style="color:rgb(15, 17, 21);">b</font>` | <font style="color:rgb(15, 17, 21);">块设备</font> | <font style="color:rgb(15, 17, 21);">硬盘、U盘等</font> |
| `<font style="color:rgb(15, 17, 21);">c</font>` | <font style="color:rgb(15, 17, 21);">字符设备</font> | <font style="color:rgb(15, 17, 21);">终端、打印机等</font> |
| `<font style="color:rgb(15, 17, 21);">s</font>` | <font style="color:rgb(15, 17, 21);">套接字</font> | <font style="color:rgb(15, 17, 21);">网络通信文件</font> |
| `<font style="color:rgb(15, 17, 21);">p</font>` | <font style="color:rgb(15, 17, 21);">管道</font> | <font style="color:rgb(15, 17, 21);">进程间通信</font> |


**<font style="color:rgb(15, 17, 21);">示例：</font>**

bash

**复制****下载**

```plain
-rwxr-xr--   # 普通文件
drwxr-xr-x   # 目录
lrwxrwxrwx   # 符号链接
```

---

<h3 id="EFKLz">**<font style="color:rgb(15, 17, 21);">权限位分解：</font>**</h3>
<h3 id="piGRh">1.</h3>
```plain
类型位   用户权限   组权限   其他用户权限
↓        ↓↓↓      ↓↓↓      ↓↓↓  
d        r w x    r - x    r - -
|        | | |    | | |    | | |
|        | | |    | | |    | | 其他用户执行权限
|        | | |    | | |    | 其他用户写权限  
|        | | |    | | |    其他用户读权限
|        | | |    | | 组执行权限
|        | | |    | 组写权限
|        | | |    组读权限
|        | | 用户执行权限
|        | 用户写权限
|        用户读权限
文件类型
```

<h3 id="qAXPY"><font style="color:rgb(15, 17, 21);">2. 文件类型位（第1位）</font></h3>
| <font style="color:rgb(15, 17, 21);">字符</font> | <font style="color:rgb(15, 17, 21);">含义</font> | <font style="color:rgb(15, 17, 21);">说明</font> |
| --- | --- | --- |
| `<font style="color:rgb(15, 17, 21);">-</font>` | <font style="color:rgb(15, 17, 21);">普通文件</font> | <font style="color:rgb(15, 17, 21);">文本文件、二进制文件、图片等</font> |
| `<font style="color:rgb(15, 17, 21);">d</font>` | <font style="color:rgb(15, 17, 21);">目录</font> | <font style="color:rgb(15, 17, 21);">文件夹</font> |
| `<font style="color:rgb(15, 17, 21);">l</font>` | <font style="color:rgb(15, 17, 21);">符号链接</font> | <font style="color:rgb(15, 17, 21);">快捷方式</font> |
| `<font style="color:rgb(15, 17, 21);">b</font>` | <font style="color:rgb(15, 17, 21);">块设备</font> | <font style="color:rgb(15, 17, 21);">硬盘、U盘等</font> |
| `<font style="color:rgb(15, 17, 21);">c</font>` | <font style="color:rgb(15, 17, 21);">字符设备</font> | <font style="color:rgb(15, 17, 21);">终端、打印机等</font> |
| `<font style="color:rgb(15, 17, 21);">s</font>` | <font style="color:rgb(15, 17, 21);">套接字</font> | <font style="color:rgb(15, 17, 21);">网络通信文件</font> |
| `<font style="color:rgb(15, 17, 21);">p</font>` | <font style="color:rgb(15, 17, 21);">管道</font> | <font style="color:rgb(15, 17, 21);">进程间通信</font> |


**<font style="color:rgb(15, 17, 21);">示例：</font>**



```plain
-rwxr-xr--   # 普通文件
drwxr-xr-x   # 目录
lrwxrwxrwx   # 符号链接
```

<h3 id="WBUU3"><font style="color:rgb(15, 17, 21);">3. 权限字符的含义</font></h3>
<h3 id="d7f217e9"><font style="color:rgb(15, 17, 21);">对于</font>**<font style="color:rgb(15, 17, 21);">文件</font>**<font style="color:rgb(15, 17, 21);">：</font></h3>
| <font style="color:rgb(15, 17, 21);">权限</font> | <font style="color:rgb(15, 17, 21);">字符</font> | <font style="color:rgb(15, 17, 21);">数字</font> | <font style="color:rgb(15, 17, 21);">含义</font> |
| --- | --- | --- | --- |
| <font style="color:rgb(15, 17, 21);">读</font> | `<font style="color:rgb(15, 17, 21);">r</font>` | <font style="color:rgb(15, 17, 21);">4</font> | <font style="color:rgb(15, 17, 21);">可以读取文件内容</font> |
| <font style="color:rgb(15, 17, 21);">写</font> | `<font style="color:rgb(15, 17, 21);">w</font>` | <font style="color:rgb(15, 17, 21);">2</font> | <font style="color:rgb(15, 17, 21);">可以修改文件内容</font> |
| <font style="color:rgb(15, 17, 21);">执行</font> | `<font style="color:rgb(15, 17, 21);">x</font>` | <font style="color:rgb(15, 17, 21);">1</font> | <font style="color:rgb(15, 17, 21);">可以执行文件（程序、脚本）</font> |


<h3 id="576cc022"><font style="color:rgb(15, 17, 21);">对于</font>**<font style="color:rgb(15, 17, 21);">目录</font>**<font style="color:rgb(15, 17, 21);">：</font></h3>
| <font style="color:rgb(15, 17, 21);">权限</font> | <font style="color:rgb(15, 17, 21);">字符</font> | <font style="color:rgb(15, 17, 21);">数字</font> | <font style="color:rgb(15, 17, 21);">含义</font> |
| --- | --- | --- | --- |
| <font style="color:rgb(15, 17, 21);">读</font> | `<font style="color:rgb(15, 17, 21);">r</font>` | <font style="color:rgb(15, 17, 21);">4</font> | <font style="color:rgb(15, 17, 21);">可以列出目录内容（需要x权限配合）</font> |
| <font style="color:rgb(15, 17, 21);">写</font> | `<font style="color:rgb(15, 17, 21);">w</font>` | <font style="color:rgb(15, 17, 21);">2</font> | <font style="color:rgb(15, 17, 21);">可以在目录中创建、删除、重命名文件（需要x权限配合）</font> |
| <font style="color:rgb(15, 17, 21);">执行</font> | `<font style="color:rgb(15, 17, 21);">x</font>` | <font style="color:rgb(15, 17, 21);">1</font> | <font style="color:rgb(15, 17, 21);">可以进入目录（cd命令）</font> |


---

<h3 id="YncDM"><font style="color:rgb(15, 17, 21);">4. 三个权限组</font></h3>
<h3 id="d63a53c0"><font style="color:rgb(15, 17, 21);">1.</font><font style="color:rgb(15, 17, 21);"> </font>**<font style="color:rgb(15, 17, 21);">用户权限 (user/owner)</font>**<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">- 位置 2-4</font></h3>
<font style="color:rgb(15, 17, 21);">文件所有者的权限</font>

<h3 id="c86f78e5"><font style="color:rgb(15, 17, 21);">2.</font><font style="color:rgb(15, 17, 21);"> </font>**<font style="color:rgb(15, 17, 21);">组权限 (group)</font>**<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">- 位置 5-7</font></h3>
<font style="color:rgb(15, 17, 21);">文件所属用户组成员的权限</font>

<h3 id="a45748a3"><font style="color:rgb(15, 17, 21);">3.</font><font style="color:rgb(15, 17, 21);"> </font>**<font style="color:rgb(15, 17, 21);">其他用户权限 (others)</font>**<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">- 位置 8-10</font></h3>
<font style="color:rgb(15, 17, 21);">系统中其他所有用户的权限</font>

**<font style="color:rgb(15, 17, 21);">示例分析：</font>**



```plain
-rwxr-xr--
↑|||||||||
|↓↓↓|↓↓↓|↓↓↓
| u | g | o
|
文件类型

u: rwx = 用户可读、写、执行
g: r-x = 组可读、执行，不可写  
o: r-- = 其他用户只可读，不可写、执行
```

---

<h3 id="y41dI"><font style="color:rgb(15, 17, 21);">5. 数字权限计算</font></h3>
<h3 id="5ace2142"><font style="color:rgb(15, 17, 21);">权限值对应：</font></h3>
+ `<font style="color:rgb(15, 17, 21);">r</font>`<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">(读) = 4</font>
+ `<font style="color:rgb(15, 17, 21);">w</font>`<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">(写) = 2</font>
+ `<font style="color:rgb(15, 17, 21);">x</font>`<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">(执行) = 1</font>
+ `<font style="color:rgb(15, 17, 21);">-</font>`<font style="color:rgb(15, 17, 21);"> </font><font style="color:rgb(15, 17, 21);">(无权限) = 0</font>

<h3 id="fdd1ff20"><font style="color:rgb(15, 17, 21);">计算方法：</font></h3>
<font style="color:rgb(15, 17, 21);">将每组权限的数值相加：</font>

**<font style="color:rgb(15, 17, 21);">示例1：</font>**`**<font style="color:rgb(15, 17, 21);">rwxr-xr--</font>**`



```plain
用户: rwx = 4+2+1 = 7
组:   r-x = 4+0+1 = 5  
其他: r-- = 4+0+0 = 4
最终权限：755
```

**<font style="color:rgb(15, 17, 21);">示例2：</font>**`**<font style="color:rgb(15, 17, 21);">rw-r--r--</font>**`



```plain
用户: rw- = 4+2+0 = 6
组:   r-- = 4+0+0 = 4
其他: r-- = 4+0+0 = 4
最终权限：644
```

---

<h3 id="dIzFe"><font style="color:rgb(15, 17, 21);">6. 常见权限模式详解</font></h3>
<h3 id="981ae5ad"><font style="color:rgb(15, 17, 21);">文件常用权限：</font></h3>


```plain
644 # rw-r--r-- : 用户可读写，其他人只读（普通文件）
755 # rwxr-xr-x : 用户全权限，其他人读执行（可执行文件）
600 # rw------- : 仅用户可读写（敏感文件）
640 # rw-r----- : 用户可读写，组可读（配置文件）
```

<h3 id="a0a2fe29"><font style="color:rgb(15, 17, 21);">目录常用权限：</font></h3>


```plain
755 # rwxr-xr-x : 用户全权限，其他人可进入和列表（普通目录）
700 # rwx------ : 仅用户可访问（私有目录）
775 # rwxrwxr-x : 用户和组全权限，其他人可进入列表（共享目录）
```

---

<h2 id="7fd282da"><font style="color:rgb(15, 17, 21);">7.</font><font style="color:rgb(15, 17, 21);"> </font>**<font style="color:rgb(15, 17, 21);">权限的实际效果演示</font>**</h2>
<h3 id="b6a273b9"><font style="color:rgb(15, 17, 21);">创建测试环境：</font></h3>


```plain
# 创建测试文件和目录
mkdir test_dir
touch test_file.txt
echo "echo 'Hello World'" > script.sh
chmod +x script.sh

# 查看权限
ls -l
```

<h3 id="697cce0a"><font style="color:rgb(15, 17, 21);">不同权限的效果：</font></h3>


```plain
# 文件权限 644 (rw-r--r--)
chmod 644 test_file.txt
ls -l test_file.txt
# -rw-r--r-- 1 user group 0 Dec 25 10:30 test_file.txt
# 效果：用户可编辑，其他人只能查看

# 文件权限 755 (rwxr-xr-x)  
chmod 755 script.sh
ls -l script.sh
# -rwxr-xr-x 1 user group 0 Dec 25 10:30 script.sh
# 效果：所有人都可以执行

# 目录权限 700 (rwx------)
chmod 700 test_dir
ls -ld test_dir
# drwx------ 2 user group 4096 Dec 25 10:30 test_dir
# 效果：只有用户可访问，其他人无法进入或查看
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760270161212-e261767b-03d2-4db2-b782-64ff3c605dfd.png)

---

<h2 id="d2584a5e"><font style="color:rgb(15, 17, 21);">8.</font><font style="color:rgb(15, 17, 21);"> </font>**<font style="color:rgb(15, 17, 21);">权限位特殊含义</font>**</h2>
<h3 id="829c51ee"><font style="color:rgb(15, 17, 21);">目录的执行权限 (</font>`<font style="color:rgb(15, 17, 21);">x</font>`<font style="color:rgb(15, 17, 21);">)：</font></h3>


```plain
# 有读无执行权限
chmod 644 test_dir
cd test_dir        # 失败：Permission denied
ls test_dir        # 失败：Permission denied

# 有执行无读权限  
chmod 311 test_dir
cd test_dir        # 成功：可以进入
ls test_dir        # 失败：无法列出内容（但可以访问已知文件）
```

<h3 id="8a5cf1f7"><font style="color:rgb(15, 17, 21);">符号链接的特殊性：</font></h3>


```plain
# 创建符号链接
ln -s /etc/passwd mylink
ls -l mylink
# lrwxrwxrwx 1 user group 11 Dec 25 10:30 mylink -> /etc/passwd

# 链接权限总是 777，实际权限由目标文件决定
```

---



<h2 id="NHcuE">2. chmod - <font style="background-color:rgba(245,245,47,1);">更改</font>文件权限</h2>
<h3 id="MsHP6">方法1：数字模式（最常用）</h3>
```bash
# 语法：chmod ABC file
# A=用户权限, B=组权限, C=其他用户权限
# r=4, w=2, x=1

chmod 755 filename    # rwxr-xr-x
chmod 644 filename    # rw-r--r--
chmod 777 filename    # rwxrwxrwx (完全开放)
chmod 600 filename    # rw------- (仅用户可读写)
```

<h3 id="gAtzm">常用数字权限：</h3>
```bash
755 # 用户：rwx，组：r-x，其他：r-x (可执行文件)
644 # 用户：rw-，组：r--，其他：r-- (普通文件)
700 # 用户：rwx，组：---，其他：--- (私有文件)
777 # 所有用户可读、写、执行 (危险！)
```

<h3 id="zt3Gg">方法2：符号模式</h3>
```bash
# 语法：chmod [who][operator][permissions] file

# who: u=用户, g=组, o=其他, a=所有
# operator: +添加, -移除, =设置
# permissions: r, w, x

chmod u+x script.sh    # 给用户添加执行权限
chmod g-w file.txt     # 移除组的写权限
chmod o=r file.txt     # 设置其他用户只有读权限
chmod a+r file.txt     # 所有用户添加读权限
chmod u=rwx,g=rx,o= file.txt  # 明确设置各权限
```

---

<h2 id="hLlKG">3. **chown** - 更改文件所有者和组</h2>
<h3 id="ozVi0">基本语法：</h3>
```bash
chown [选项] 用户[:组] 文件...
```

<h3 id="T0LzJ">常用选项：</h3>
```bash
chown user filename           # 更改文件所有者
chown :group filename         # 更改文件所属组
chown user:group filename     # 同时更改所有者和组
chown -R user:group directory # 递归更改目录下所有文件
```

<h3 id="v4jzS">实用示例：</h3>
```bash
chown alice file.txt              # 将文件所有者改为 alice
chown :developers project/        # 将目录组改为 developers
chown bob:staff document.pdf      # 同时更改所有者和组
chown -R www-data:www-data /var/www  # 递归更改网站目录权限
sudo chown root:root /etc/passwd  # 需要sudo更改系统文件
```

---

<h2 id="OAKP2">4. **ls -L** - 理解链接文件权限</h2>
<h3 id="jKLp8">查看链接文件：</h3>
```bash
ls -l linkname
# 输出示例：lrwxrwxrwx 1 user group 11 Dec 25 10:30 mylink -> targetfile
```

<h3 id="vJVoo">链接文件权限特点：</h3>
+ 链接文件的权限总是 `lrwxrwxrwx`（所有用户都有全部权限）
+ 实际权限由**目标文件**的权限决定
+ 链接文件只是指向实际文件的快捷方式

<h3 id="JSqEk">示例：</h3>
```bash
# 创建链接
ln -s /etc/passwd passwd_link

# 查看链接
ls -l passwd_link
# lrwxrwxrwx 1 user group 11 Dec 25 10:30 passwd_link -> /etc/passwd

# 实际权限由目标文件 /etc/passwd 决定
ls -l /etc/passwd
# -rw-r--r-- 1 root root 2550 Dec 24 08:00 /etc/passwd
```

---

<h2 id="x8NWr">5. **权限管理实战示例**</h2>
<h3 id="ZrsDI">场景1：设置网站文件权限</h3>
```bash
# 1. 查看当前权限
ls -la /var/www/html/

# 2. 更改所有者为web服务器用户
sudo chown -R www-data:www-data /var/www/html/

# 3. 设置安全权限
sudo chmod -R 755 /var/www/html/    # 目录可执行
sudo chmod -R 644 /var/www/html/*.html  # 文件只读
sudo chmod 755 /var/www/html/cgi-bin/   # CGI目录可执行
```

<h3 id="UcRRf">场景2：设置私有配置文件</h3>
```bash
# 创建配置文件
touch ~/.ssh/config

# 设置只有用户可读写
chmod 600 ~/.ssh/config

# 验证权限
ls -l ~/.ssh/config
# -rw------- 1 user user 0 Dec 25 10:30 /home/user/.ssh/config
```

<h3 id="MfIFe">场景3：共享项目目录</h3>
```bash
# 创建项目目录
mkdir /home/project

# 设置组共享
sudo chown -R alice:developers /home/project
sudo chmod -R 775 /home/project

# 结果：alice和developers组成员都可读写执行
```

---

<h2 id="oayQ5">6. **特殊权限**</h2>
<h3 id="BNEiC">SetUID, SetGID, Sticky Bit：</h3>
```bash
chmod u+s file        # SetUID：以文件所有者身份执行
chmod g+s directory   # SetGID：在目录中创建的文件继承组
chmod +t directory    # Sticky Bit：只有文件所有者能删除

# 数字表示：
chmod 4755 file       # SetUID (4)
chmod 2755 directory  # SetGID (2)  
chmod 1755 directory  # Sticky Bit (1)
```

<h3 id="YugaV">特殊权限示例：</h3>
```bash
# /tmp 目录的典型权限
ls -ld /tmp
# drwxrwxrwt 10 root root 4096 Dec 25 10:30 /tmp
# ↑ Sticky Bit 防止用户删除他人的临时文件
```

---

<h2 id="kQSbO">7. **权限检查与调试**</h2>
<h3 id="n0XFo">检查当前用户权限：</h3>
```bash
# 查看当前用户和组
whoami
groups

# 检查对文件的权限
ls -l file.txt
test -r file.txt && echo "可读" || echo "不可读"
test -w file.txt && echo "可写" || echo "不可写" 
test -x file.txt && echo "可执行" || echo "不可执行"
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760279026105-ec5168db-f66f-4816-ae97-681efd537005.png)![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760279051954-913d29db-3be8-49b1-a880-b6a35366fc9d.png)

<h3 id="bLuuU">权限问题排查：</h3>
```bash
# 1. 查看文件权限
ls -l problem_file

# 2. 查看用户所属组
groups $USER

# 3. 检查父目录权限
ls -ld $(dirname problem_file)

# 4. 使用namei查看完整路径权限
namei -l /path/to/file
```

---

<h2 id="WCFeO">8. **安全最佳实践**</h2>
1. **最小权限原则**：只给予必要的权限
2. **文件 vs 目录权限**：
    - 文件：644 (普通), 755 (可执行)
    - 目录：755 (需要x权限才能进入)
3. **敏感文件**：600 (仅用户可读写)
4. **避免777**：除非完全了解风险
5. **定期检查**：使用 `find` 查找异常权限

```bash
find /home -perm /o+w -ls    # 查找其他用户可写的文件
find / -type f -perm /4000 -ls  # 查找SetUID文件
```

这些权限管理命令是 Linux 系统安全的基础，熟练掌握它们对系统管理和安全至关重要！

好的！我来为您详细解释 Linux 进程控制的相关命令。

<h1 id="H1q5v">四。进程控制🧸🧸</h1>
<h3 id="Au64P">1. ps - 查看进程状态基本语法：  
</h3>


<h3 id="NGaEP">基本语法：</h3>
```bash
ps [选项]
```

<h3 id="eVbvi">常用选项组合：</h3>
```bash
ps aux        # 查看系统所有进程（最常用）
ps -ef        # 完整格式显示所有进程
ps -u username # 查看指定用户的进程
ps -p PID     # 查看指定PID的进程
ps --forest   # 显示进程树状结构
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760279129281-d99d52bc-be3f-4844-a1f2-a0175b27aee8.png)

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760279229601-dbf6a005-d468-4035-abad-a9374367a898.png)

<h3 id="yi9ad">详细解释 `ps aux` 输出：</h3>
```bash
USER    PID %CPU %MEM    VSZ   RSS TTY    STAT START   TIME COMMAND
root      1  0.0  0.1 169284 13156 ?      Ss   10:30   0:01 /sbin/init
user   1234  1.2  2.1 1023448 215644 pts/0 Sl   10:31   0:05 chrome
```

**各字段含义：**

+ `USER`：进程所有者
+ `PID`：进程ID（唯一标识）
+ `%CPU`：CPU使用率
+ `%MEM`：内存使用率
+ `VSZ`：虚拟内存大小（KB）
+ `RSS`：物理内存大小（KB）
+ `TTY`：终端类型（?表示无终端）
+ `STAT`：进程状态
+ `START`：启动时间
+ `TIME`：累计CPU时间
+ `COMMAND`：命令名称

<h3 id="Fc2jH">进程状态（STAT）详解：</h3>
| 状态 | 含义 |
| --- | --- |
| `R` | 运行中 (Running) |
| `S` | 睡眠中 (Sleeping) |
| `D` | 不可中断睡眠 (Disk I/O) |
| `T` | 已停止 (Stopped) |
| `Z` | 僵尸进程 (Zombie) |
| `<` | 高优先级 |
| `N` | 低优先级 |
| `s` | 会话领导者 |
| `+` | 前台进程组 |


<h3 id="XpjeO">实用示例：</h3>
```bash
ps aux | grep chrome          # 查找chrome相关进程
ps -u $USER                   # 查看当前用户的所有进程
ps --ppid 1234                # 查看父进程为1234的所有子进程
ps -eo pid,ppid,cmd --forest  # 树状显示进程关系
```

---

<h2 id="eoTk6">2. **kill** - 终止进程</h2>
<h3 id="Eh1Zx">基本语法：</h3>
```bash
kill [信号] PID
killall [信号] 进程名
pkill [选项] 模式
```

<h3 id="ypCDo">常用信号：</h3>
| 信号 | 数字 | 含义 | 用途 |
| --- | --- | --- | --- |
| `SIGTERM` | 15 | 终止信号（默认） | 正常终止进程 |
| `SIGKILL` | 9 | 强制终止 | 立即杀死进程 |
| `SIGHUP` | 1 | 挂起信号 | 重新加载配置 |
| `SIGSTOP` | 17,19,23 | 暂停进程 | 调试用途 |


<h3 id="ybkEO">使用示例：</h3>
```bash
# 正常终止进程（推荐先尝试）
kill 1234
kill -15 1234

# 强制终止进程（无法捕获或忽略）
kill -9 1234
kill -KILL 1234

# 按进程名终止
killall chrome
killall -9 firefox

# 按模式终止
pkill -f "python script.py"
pkill -u username chrome

# 列出所有信号
kill -l
```

<h3 id="DUjjt">安全终止流程：</h3>
```bash
# 1. 先尝试正常终止
kill PID

# 2. 等待几秒后检查进程是否结束
ps -p PID

# 3. 如果还在运行，使用强制终止
kill -9 PID

# 4. 确认进程已终止
ps -p PID
```

---

<h2 id="deJLv">3. **top** - 动态查看系统状态</h2>
<h3 id="FLIKO">启动命令：</h3>
```bash
top          # 基本视图
top -u username  # 只看指定用户的进程
top -p PID1,PID2 # 只看指定PID的进程
```

![](https://cdn.nlark.com/yuque/0/2025/png/61614341/1760279303373-53dadd88-5047-4cff-a6df-fdc6f4024912.png)

<h3 id="VtHsi">top 界面详解：</h3>
```plain
top - 10:30:00 up 1 day,  2:30,  1 user,  load average: 0.05, 0.10, 0.15
Tasks: 250 total,   1 running, 249 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.5 us,  1.0 sy,  0.0 ni, 96.5 id,  0.0 wa,  0.0 hi,  0.0 si
MiB Mem :  15982.5 total,   1024.5 free,   8192.0 used,   6766.0 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   7520.5 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 1234 user      20   0 1023448 215644  45632 S   1.2   2.1   0:05.23 chrome
    1 root      20   0  169284  13156   8324 S   0.0   0.1   0:01.23 systemd
```

<h3 id="kasPC">top 交互命令（在 top 运行时按）：</h3>
| 按键 | 功能 |
| --- | --- |
| `h` | 显示帮助 |
| `q` | 退出 top |
| `k` | 终止进程（输入PID和信号） |
| `r` | 更改进程优先级（renice） |
| `P` | 按CPU使用率排序 |
| `M` | 按内存使用率排序 |
| `T` | 按运行时间排序 |
| `1` | 显示所有CPU核心的详细状态 |
| `u` | 只显示指定用户的进程 |
| `z` | 彩色/黑白显示切换 |


<h3 id="b5gEv">关键信息解读：</h3>
+ **load average**：系统负载（1分钟、5分钟、15分钟平均值）
+ **%Cpu(s)**：
    - `us`：用户空间CPU占用
    - `sy`：内核空间CPU占用  
    - `id`：空闲CPU
    - `wa`：等待I/O的CPU
+ **Tasks**：进程统计（运行、睡眠、停止、僵尸）

---

<h2 id="kivPa">4. **systemctl** - 系统服务管理</h2>
<h3 id="rTqcM">基本语法：</h3>
```bash
systemctl [命令] [服务名]
```

<h3 id="U7lGu">服务状态管理：</h3>
```bash
# 启动服务
systemctl start servicename

# 停止服务
systemctl stop servicename

# 重启服务
systemctl restart servicename

# 重新加载配置（不重启）
systemctl reload servicename

# 查看服务状态
systemctl status servicename

# 启用开机自启
systemctl enable servicename

# 禁用开机自启
systemctl disable servicename

# 检查是否启用
systemctl is-enabled servicename
```

<h3 id="JQpzv">服务状态查看：</h3>
```bash
# 查看所有服务状态
systemctl list-units --type=service

# 查看运行中的服务
systemctl list-units --type=service --state=running

# 查看失败的服务
systemctl list-units --type=service --state=failed

# 查看服务依赖关系
systemctl list-dependencies servicename
```

<h3 id="FLf7T">常用服务示例：</h3>
```bash
# Web服务器
systemctl status nginx
systemctl restart apache2

# 数据库
systemctl start mysql
systemctl stop postgresql

# SSH服务
systemctl enable ssh
systemctl status sshd

# 系统服务
systemctl reboot    # 重启系统
systemctl poweroff  # 关闭系统
systemctl suspend   # 挂起系统
```

---

<h2 id="lEB3g">5. **综合实战示例**</h2>
<h3 id="yLWpi">场景1：排查高CPU占用进程</h3>
```bash
# 1. 使用 top 查看资源占用
top

# 2. 按 P 按CPU排序，找到问题PID
# 3. 查看进程详细信息
ps -p 1234 -o pid,ppid,user,%cpu,%mem,cmd

# 4. 终止问题进程
kill 1234

# 5. 如果普通终止无效，强制终止
kill -9 1234
```

<h3 id="Ea2rr">场景2：管理系统服务</h3>
```bash
# 1. 检查Web服务器状态
systemctl status nginx

# 2. 如果停止，启动服务
systemctl start nginx

# 3. 设置开机自启
systemctl enable nginx

# 4. 测试服务是否正常
curl -I http://localhost

# 5. 查看服务日志
journalctl -u nginx -f
```

<h3 id="s7uVB">场景3：批量管理进程</h3>
```bash
# 查找并终止所有chrome进程
ps aux | grep chrome | awk '{print $2}' | xargs kill

# 或者使用 pkill
pkill chrome

# 终止用户的所有进程（谨慎使用！）
pkill -u username
```

<h3 id="kNN1A">场景4：监控系统资源</h3>
```bash
# 实时监控
top

# 每2秒刷新一次，只看前10个进程
top -d 2 -n 1 | head -20

# 监控特定进程
watch -n 1 'ps -p 1234 -o pid,%cpu,%mem,cmd'
```

---

<h2 id="Coa0B">6. **相关工具补充**</h2>
<h3 id="SC9Ex">**htop**（增强版 top）：</h3>
```bash
# 安装
sudo apt install htop

# 使用
htop
```

<h3 id="rh9eu">**pstree**（进程树）：</h3>
```bash
pstree          # 显示进程树
pstree -p       # 显示PID
pstree -u       # 显示用户
```

<h3 id="NY7PT">**nice/renice**（调整优先级）：</h3>
```bash
# 启动低优先级进程
nice -n 10 command

# 调整运行中进程的优先级
renice -n 5 -p 1234
```

这些进程控制命令是系统管理和故障排查的基础工具，熟练掌握它们对维护系统稳定性非常重要！

好的！我来为您详细解释这些 Linux 核心概念和工具。

<h2 id="aSuzf">五。理解</h2>
<h2 id="QE4hE">1. **理解"Linux 中一切皆文件"的哲学**</h2>
<h3 id="fcG2n">核心思想：</h3>
在 Linux 中，几乎所有资源都被抽象为文件，可以通过文件操作接口来访问。

<h3 id="GiSdd">具体体现：</h3>
```bash
# 普通文件
ls -l /home/user/document.txt

# 目录（特殊文件）
ls -ld /etc

# 设备文件
ls -l /dev/sda1          # 块设备（硬盘分区）
ls -l /dev/ttyS0         # 字符设备（串口）

# 进程信息（虚拟文件系统）
cat /proc/cpuinfo        # CPU信息
cat /proc/meminfo        # 内存信息
ls /proc/1234/           # 进程1234的信息

# 网络连接
cat /proc/net/tcp        # TCP连接信息

# 系统配置
cat /sys/class/net/eth0/operstate  # 网卡状态
```

<h3 id="mj0fs">统一操作接口：</h3>
```bash
# 都用相同的命令操作
echo "hello" > file.txt          # 写入普通文件
echo "1" > /sys/class/leds/led0/brightness  # 控制LED灯
cat /proc/loadavg                # 读取系统负载
```

---

<h2 id="NhQNO">2. **文件系统结构**</h2>
<h3 id="p5Oh4">主要目录作用：</h3>
| 目录 | 用途 | 示例内容 |
| --- | --- | --- |
| `/` | 根目录 | 所有目录的起点 |
| `/home` | 用户主目录 | `/home/username/` |
| `/etc` | 配置文件 | `passwd`, `hosts`, `nginx/` |
| `/var` | 可变数据 | `logs/`, `www/`, `mail/` |
| `/tmp` | 临时文件 | 程序运行时临时文件 |
| `/usr` | 用户程序 | `bin/`, `lib/`, `share/` |
| `/bin` | 基本命令 | `ls`, `cp`, `mv` |
| `/dev` | 设备文件 | `sda1`, `ttyS0`, `null` |
| `/proc` | 进程信息 | 虚拟文件系统 |
| `/opt` | 可选软件 | 第三方应用程序 |
| `/boot` | 启动文件 | 内核、引导程序 |


<h3 id="kHwcw">绝对路径 vs 相对路径：</h3>
**绝对路径**：从根目录开始

```bash
cd /home/user/documents
ls /etc/nginx/nginx.conf
cat /var/log/syslog
```

**相对路径**：从当前目录开始

```bash
cd documents          # 进入当前目录下的documents
ls ../downloads       # 查看上级目录的downloads
cat ./config.txt      # 查看当前目录的config.txt
```

<h3 id="msDoF">特殊路径符号：</h3>
```bash
.          # 当前目录
..         # 上级目录
~          # 当前用户主目录
-          # 上一个工作目录
```

---

<h2 id="al4ju">3. **基础服务管理（systemd）与网络配置**</h2>
<h3 id="MWB73">systemd 服务管理：</h3>
```bash
# 服务状态管理
sudo systemctl start nginx
sudo systemctl stop nginx
sudo systemctl restart nginx
sudo systemctl reload nginx     # 重新加载配置
sudo systemctl status nginx

# 开机自启管理
sudo systemctl enable nginx
sudo systemctl disable nginx
sudo systemctl is-enabled nginx

# 查看所有服务
systemctl list-units --type=service
systemctl list-unit-files --type=service
```

<h3 id="Wb3gs">网络配置：</h3>
```bash
# 查看网络接口
ip addr show
ifconfig        # 旧命令

# 查看路由表
ip route show
route -n

# 网络连通性测试
ping google.com
traceroute google.com

# 端口监听检查
netstat -tulnp
ss -tulnp

# DNS查询
nslookup google.com
dig google.com
```

<h3 id="nSUSC">网络配置文件：</h3>
```bash
# Ubuntu/Debian
/etc/netplan/01-netcfg.yaml

# CentOS/RHEL
/etc/sysconfig/network-scripts/ifcfg-eth0

# DNS配置
/etc/resolv.conf

# 主机名
/etc/hostname
/etc/hosts
```

---

<h2 id="KLYJ7">4. **Vim 编辑器入门**</h2>
<h3 id="t7wQt">三种模式：</h3>
1. **普通模式**（Normal）：移动光标、删除、复制粘贴
2. **插入模式**（Insert）：输入文本
3. **命令模式**（Command）：保存、退出、搜索等

<h3 id="dNgoW">模式切换：</h3>
```bash
vim filename        # 用vim打开文件（进入普通模式）

# 模式切换
i                  # 普通→插入（在光标前）
a                  # 普通→插入（在光标后）
o                  # 普通→插入（新行）
ESC                # 插入→普通
:                  # 普通→命令
```

<h3 id="n727L">基本操作：</h3>
**普通模式命令：**

```bash
# 光标移动
h j k l            # 左 下 上 右
w b                # 下一个词 / 上一个词
0 $                # 行首 / 行尾
gg G               # 文件开头 / 文件结尾

# 编辑操作
x                  # 删除字符
dd                 # 删除整行
yy                 # 复制整行
p                  # 粘贴
u                  # 撤销
Ctrl + r           # 重做

# 搜索
/pattern           # 向前搜索
?pattern           # 向后搜索
n N                # 下一个 / 上一个匹配
```

**命令模式命令：**

```bash
:w                 # 保存
:q                 # 退出
:q!                # 强制退出（不保存）
:wq                # 保存并退出
:x                 # 保存并退出

:set number        # 显示行号
:set nonumber      # 隐藏行号
:s/old/new/g       # 替换当前行
:%s/old/new/g      # 替换整个文件
```

---

<h2 id="andSc">5. **常用命令行工具**</h2>
<h3 id="ufaE3">**grep** - 文本搜索：</h3>
```bash
grep "pattern" file.txt           # 基本搜索
grep -r "pattern" directory/      # 递归搜索
grep -i "pattern" file.txt        # 忽略大小写
grep -v "pattern" file.txt        # 反向匹配
grep -n "pattern" file.txt        # 显示行号
grep -E "pattern1|pattern2" file.txt  # 扩展正则表达式
```

<h3 id="u3GFZ">**awk** - 文本处理：</h3>
```bash
# 基本用法
awk '{print $1}' file.txt         # 打印第一列
awk -F: '{print $1}' /etc/passwd  # 指定分隔符为冒号

# 条件处理
awk '$3 > 1000 {print $1}' file.txt  # 第三列大于1000时打印第一列
awk '/pattern/ {print $0}' file.txt  # 匹配模式的行

# 统计
awk '{sum += $1} END {print sum}' file.txt  # 求和
awk '{count++} END {print count}' file.txt  # 行数统计
```

<h3 id="AjnD1">**sed** - 流编辑器：</h3>
```bash
sed 's/old/new/g' file.txt        # 替换文本
sed 's/old/new/2' file.txt        # 只替换每行第二个匹配
sed '5d' file.txt                 # 删除第5行
sed '1,5d' file.txt               # 删除1-5行
sed '/pattern/d' file.txt         # 删除匹配行
sed -n '5,10p' file.txt           # 打印5-10行
sed -i 's/old/new/g' file.txt     # 直接修改文件
```

<h3 id="wmbEj">**tmux** - 终端复用器：</h3>
```bash
# 会话管理
tmux new -s session_name          # 新建会话
tmux attach -t session_name       # 连接会话
tmux ls                           # 列出会话
tmux kill-session -t session_name # 终止会话

# 窗口管理（在tmux中按 Ctrl+b 后）
c                  # 新建窗口
n p                # 下一个/上一个窗口
0-9                # 切换到指定窗口
,                  # 重命名窗口

# 面板管理
%                  # 垂直分割
"                  # 水平分割
方向键              # 切换面板
x                  # 关闭面板
```

---

<h2 id="HXlci">6. **Linux 内核基础（选学）**</h2>
<h3 id="Pqknj">进程调度：</h3>
```bash
# 查看进程优先级
ps -eo pid,comm,ni,pri

# 调整进程优先级
nice -n 10 command        # 启动低优先级进程
renice -n 5 -p 1234       # 调整运行中进程优先级

# 查看调度策略
chrt -p 1234
```

<h3 id="LVf1r">内存管理：</h3>
```bash
# 内存信息
free -h
cat /proc/meminfo

# 内存页面大小
getconf PAGESIZE

# 查看内存映射
pmap 1234
cat /proc/1234/maps
```

<h3 id="QG9bP">设备驱动：</h3>
```bash
# 查看加载的模块
lsmod
cat /proc/modules

# 模块信息
modinfo module_name

# 加载/卸载模块
sudo modprobe module_name
sudo rmmod module_name

# 设备信息
lspci                    # PCI设备
lsusb                    # USB设备
lscpu                    # CPU信息
```

<h3 id="d26yt">系统监控工具：</h3>
```bash
# 性能监控
vmstat 1                # 虚拟内存统计
iostat 1                # I/O统计
mpstat 1                # CPU统计
pidstat 1               # 进程统计

# 高级工具
perf record -g command  # 性能分析
strace -p 1234          # 系统调用跟踪
```

---

<h2 id="Q44Sf">7. **综合实战示例**</h2>
<h3 id="tVIfb">场景1：系统问题排查</h3>
```bash
# 1. 检查系统负载
cat /proc/loadavg

# 2. 查看内存使用
free -h

# 3. 找出高CPU进程
ps aux --sort=-%cpu | head -10

# 4. 检查磁盘空间
df -h

# 5. 查看系统日志
sudo tail -f /var/log/syslog
```

<h3 id="sG6Ci">场景2：文本处理流水线</h3>
```bash
# 分析日志文件
grep "ERROR" /var/log/app.log | \
awk '{print $1, $2, $5}' | \
sort | \
uniq -c | \
sort -nr | \
head -10
```

<h3 id="My1rn">场景3：服务部署脚本</h3>
```bash
#!/bin/bash
# 停止服务
sudo systemctl stop myapp

# 备份配置
cp /etc/myapp/config.conf /etc/myapp/config.conf.backup

# 更新配置
sed -i 's/old_host/new_host/g' /etc/myapp/config.conf

# 启动服务
sudo systemctl start myapp
sudo systemctl enable myapp

# 检查状态
sudo systemctl status myapp
```

这些是 Linux 系统管理和开发的核心技能，熟练掌握它们将大大提高您的工作效率！

