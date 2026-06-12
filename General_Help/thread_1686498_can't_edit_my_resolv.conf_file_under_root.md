---
title: "can't edit my resolv.conf file under root"
date: 2011-02-12
forum: General Help
---

### Post by gilloz on 2011-02-12
I am trying to edit my /etc/resolv.conf file while under root.  After saving the changes and reboot my computer, file has not changed.  I read a thread on chattr and lsattr on this fourm.(see link below)  I ran in terminal lsattr /etc/resolv.conf and got the following results:
-----------------e- /etc/resolv.conf
What does the dashes and e mean?  I thought I would get ----ia------------ /etc/resolv.conf instead, as shown in the link.  What am I doing wrong???

Ref. ([http://ubuntuforums.org/showthread.php?t=1509499&page=2](http://ubuntuforums.org/showthread.php?t=1509499&page=2))

---

### Post by gordintoronto on 2011-02-12
resolv.conf is created by Network Manager during the boot process. Change the settings in Network Manager to have something different in resolv.conf.

---

### Post by gilloz on 2011-02-12
Thanks for your reply.  Now, can you tell me how to access the Network Manager for 10.04.1?  Can't find it so far.

---

### Post by gordintoronto on 2011-02-12
System/Preferences/Network Connections

---

### Post by wojox on 2011-02-12
Are you trying to change your DNS?

---

