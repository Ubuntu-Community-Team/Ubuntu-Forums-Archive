---
title: "Backup Wubi Files in Windows XP"
date: 2011-03-17
forum: General Help
---

### Post by Singer on 2011-03-17
guys my ubuntu 10.10 got messed up due to power failure in the event of updating the synaptic package files.As i bootup now the log in screen comes but the keyboard/mouse is not responsive(i am using a dell laptop) As i have some important info saved in ubuntu home folder i need to recollect it so that i can make a fresh install of ubuntu once again. is there anyway to backup those files so that i can use them on windows xp or later on ubuntu?? i tried searching the web but came up with totally confusing results.

---

### Post by bcbc on 2011-03-17
Try this [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Download and run - then point it at the virtual disk (c:\ubuntu\disks\root.disk) and you get read only access to copy off data. (change drive if not on c:)

You can also boot an Ubuntu live CD and loop mount it. See the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") for details:

---

### Post by Singer on 2011-03-17
> **bcbc said:**
> Try this [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Download and run - then point it at the virtual disk (c:\ubuntu\disks\root.disk) and you get read only access to copy off data. (change drive if not on c:)

You can also boot an Ubuntu live CD and loop mount it. See the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") for details:

thankyou soo much BCBC it has helped me

---

