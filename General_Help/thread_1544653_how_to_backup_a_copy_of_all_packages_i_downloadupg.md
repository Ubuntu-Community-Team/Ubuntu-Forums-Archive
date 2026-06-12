---
title: "how to backup a copy of all packages i download/upgrade...?"
date: 2010-08-02
forum: General Help
---

### Post by OnlineBuddy on 2010-08-02
i want to keep a backup copy of all packages i have downloaded/upgraded. so that i dont have to go *ONLINE*  everytime i have to reinstall.....i have a (per MB plan)
.
i am using ubuntu 10.04
.
someone suggested me following code->
********************************************************************
Open a terminal and paste the following into it:
$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`the last command will take some time)

RE-INSTALL
Code:
sudo dpkg -i *.deb
**********************************************************************
BUT IT WRECKED MY SYSTEM(specially tomcat didnt work at all!!), AND MANY PACKAGES WERE  REPORTED BROKEN
.
.
[SIZE=2]
[/SIZE][SIZE=2]**NOTE->** i want to bring this to everyone's notice(**specially ubuntu guru's**) that i am having a **really hard time** convincing my friends to switch over to ubuntu....PRIMARILY because i told them they had to go online(to install pkgs) even if they had to watch a video!! with WINDOWS we have all have a folder of essential s/w which we quickly installed in case we had to reinstall windows!! 

**please consider!!-**in my country **net** is very expensive and mostly on (**per MB**) plans....so it is a **  ***MAJOR***  **turn off to ubuntu switchers!!!! 
......
......

SO IS THERE A WAY THAT **ONLY ONE** OF US COULD GO ONLINE AND DOWNLOAD ALL PACKAGES/UPDATES AND **SHARE THEM** OR KEEP THEM AS A **BACKUP** OR SEND THEM TO SOMEONE WHO DOSEN'T HAVE A NET CONNECTION!!!.....
.......
.......


 
[/SIZE]

---

### Post by OnlineBuddy on 2010-08-02
.....
also is there a way to restore your system similar to (**SYSTEM RESTORE  **in windows)...

---

### Post by 101011010010 on 2010-08-02
Hello, most if not all installed packages can be found in,> /var/cache/apt/archives You can just copy them.
This post with help you create a list of all installed applicants, which can be used to reinstall all the packages after a clean install, it might come in handy at some point.[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
I hope this helps.

---

### Post by OnlineBuddy on 2010-08-02
> **101011010010 said:**
> Hello, most if not all installed packages can be found in, You can just copy them.
This post with help you create a list of all installed applicants, which can be used to reinstall all the packages after a clean install, it might come in handy at some point.[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)
I hope this helps.
thanksss a lot man!!!...
.
just need to clear one more thing.....could i turn a folder into a repository??..so SYNAPTIC would first search that folder and then go online.....
i know something like that could be done with CD....

---

### Post by 101011010010 on 2010-08-02
That's what happens anyway. Synaptic reads /var/cache/apt/archives and then checks online. So put what you want in apt/archives and that should do the trick. This link has a lot of useful info you might find helpful. 

[http://ubuntuforums.org/showthread.php?t=352460&highlight=aptcd](http://ubuntuforums.org/showthread.php?t=352460&highlight=aptcd). 
Good luck.

---

