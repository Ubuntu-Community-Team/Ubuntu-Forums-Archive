---
title: "New to ubunto"
date: 2006-04-22
forum: General Help
---

### Post by xwindows2 on 2006-04-22
Hi I just installed ubunto 6.06 beta drapper,I am new to Linux
 I like this one..Have a question what is the easyest way to load nvidia driver?
The sys is amd 1300.. ram 512.. vid card pny gforce 5200..
Do i still need  to edit  config file , i did download latest driver from nvidia
please help

---

### Post by dermotti on 2006-04-22
Its Ubuntu, not ubunto. And its Dapper, not drapper.

Easiest way is running **sudo apt-get install nvidia-glx ** then when thats alll done run **sudo dpkg-reconfigure xserver-xorg** and select nvidia as your driver.

---

### Post by Mustard on 2006-04-22
Doing this after installing nvidia-glx should configure xorg.conf to use nvidia, **sudo nvidia-glx-config enable**, if it fails then you could move to the second command shown above.

---

### Post by xwindows2 on 2006-04-23
Hi there i am still un sure where to start with installing nvidia driver
not sure about   sudo , do you use that comand when your in xorg.config.
 Is there some one then can list all the steps in order.
this may be asking alot,however not sure where to start..

---

### Post by Mustard on 2006-04-23
Ubuntu Wiki
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) 

Ubuntu Forums
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

Root and Sudo
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ubuntu27 on 2006-04-23
[QUOTE=xwindows2]Hi there i am still un sure where to start with installing nvidia driver
not sure about   sudo , do you use that comand when your in xorg.config.
 Is there some one then can list all the steps in order.
this may be asking alot,however not sure where to start..[/QUOTE]

When they/we say that you have to type a command or whenever you see apt, it have to be written in the Terminal.

You can find the Terminal in  Applications/Accesories/Terminal



@Moderators: This need to be moved to Dapper Drake Dev. Forum ;)

---

