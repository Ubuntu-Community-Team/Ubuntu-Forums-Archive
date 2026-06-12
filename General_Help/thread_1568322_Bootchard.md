---
title: "Bootchard"
date: 2010-09-05
forum: General Help
---

### Post by sharathcshekhar on 2010-09-05
Hi All,
How do I disable Bootchartd to start up my system without uninstalling it? I want to disable it firstly because I think that will make the boot up process slightly slower, secondly my /var/log/bootchart is getting more and more dense.
I tried the below link, but it did not work and bootchart was still creating the boot images:(
[http://ubuntuforums.org/showthread.php?t=868189]("http://ubuntuforums.org/showthread.php?t=868189")
I also tried to removing bootchard from all run levels using sysv-rc-conf. But surprisingly that had not effect :(
I had to finally remove it. Now, bootchartd is not creating any charts in /var/log/bootchart, but I can see s message pop up about bootchat on terminal during boot up. I tried to grep for what exactly that message is in syslog and dmesg. But I could not find it. 
I would appreciate any help. Thanks a lot in advance.
I am running Lucid-i386.

---

### Post by sharathcshekhar on 2010-09-08
Surprising, nobody is answering this!! Can some bootchart expert help please?

---

