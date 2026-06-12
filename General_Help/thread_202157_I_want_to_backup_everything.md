---
title: "I want to backup everything"
date: 2006-06-22
forum: General Help
---

### Post by CameronCalver on 2006-06-22
Hello i have a couple of restart in my time with ubuntu andi  have ifnally got it set up perfectly so how can i backup all the things that i have like my /home/cameron and all the cionfig s ihave changesd and all thing i have downloadedi n synaptic and apt-get so if something goes wrong i can just extract the files do a restart and everything will be back including thing in applications
Thanks, Cameron

---

### Post by thk on 2006-06-23
Take a look at the mondo rescue suite.

---

### Post by pclancy on 2006-06-23
I thought this thread did a very good job of explaining how to back things up: 
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I'm not sure if this is exactly what you're looking for, but it is one way to go.

---

### Post by aysiu on 2006-06-23
Use PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

and consider making a /home partition:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by CameronCalver on 2006-06-23
[QUOTE=pclancy]I thought this thread did a very good job of explaining how to back things up: 
[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I'm not sure if this is exactly what you're looking for, but it is one way to go.[/QUOTE]

thanks i am backing it up now and i did not really want to mess around with paritions

---

### Post by CameronCalver on 2006-06-23
pclancy i get this error 

/opt/linuxdcpp/build/gui/wulfor.o
/opt/linuxdcpp/build/gui/mainwindow.o
/opt/linuxdcpp/build/gui/bookentry.o
/opt/linuxdcpp/build/gui/wulformanager.o
/opt/linuxdcpp/build/gui/selecter.o
/opt/linuxdcpp/.sconsign
/opt/linuxdcpp/dcpp
/opt/linuxdcpp/config.log
/opt/linuxdcpp/SConstruct
/opt/linuxdcpp/Readme.txt
/opt/linuxdcpp/License.txt
/opt/linuxdcpp/Credits.txt
/opt/linuxdcpp/Changelog.txt
/initrd/
/vmlinuz
/debootstrap/
/debootstrap/debootstrap.log
/usplash_fifo
/initrd.img.old
/vmlinuz.old
tar: --exclude=/proc: Cannot stat: No such file or directory
tar: --exclude=/lost+found: Cannot stat: No such file or directory
tar: --exclude=/backup.tgz: Cannot stat: No such file or directory
tar: --exclude=/mnt: Cannot stat: No such file or directory
tar: --exclude=/sys: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
root@ubuntu:/#

---

