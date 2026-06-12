---
title: "sudo node command not found"
date: 2011-02-25
forum: General Help
---

### Post by apantev on 2011-02-25
I just installed node.js and it is located at /home/apantev/local/node/bin . So I added the follow to my ~/.bashrc

```
export PATH=/home/apantev/local/node/bin:$PATH
```And this works fine if I use node normally for instance ```
node -v
v0.4.1
```, but If I try to use sudo with it I get:

```
sudo node -v
sudo: node: command not found
```Does anyone know how to make sudo find the command? I don't want to have to give sudo the full path everytime.

---

### Post by Smart Viking on 2011-02-25
Try
```
$ sudo su
# node -v
```instead.

---

### Post by apantev on 2011-02-25
Well that does work and its way better than before, but is there any way to do it without having to do sudo su.

---

### Post by hawkmage on 2011-02-25
That is a very odd response.  What do you get when you run the following:
```
which node
ls -l `which node`
```

---

### Post by 3rdalbum on 2011-02-25
Add the 'export' line to /root/.bashrc, and make sure the target file  is executable by root.

---

### Post by hawkmage on 2011-02-25
> **3rdalbum said:**
> Add the 'export' line to /root/.bashrc, and make sure the target file  is executable by root.
Since the:
```
$ sudo su
# node -v
```
worked I would say that root can execute "node".

---

### Post by Joeb454 on 2011-02-25
I believe ```
sudo su
``` will retain your current PATH, hence why it worked.

Adding it to /root/.bashrc as mentioned above would mean sudo should work too

---

### Post by hawkmage on 2011-02-25
Running something through sudo uses your current path to find the executable not roots.  
```
hawkmage@ubuntu:~$ echo ${PATH}
/home/hawkmage/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
hawkmage@ubuntu:~$ sudo echo ${PATH}
/home/hawkmage/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
hawkmage@ubuntu:~$ sudo su -
root@ubuntu:~# echo ${PATH}
/bin:/usr/bin:/sbin:/usr/sbin
root@ubuntu:~# exit
logout
hawkmage@ubuntu:~$
```

---

