---
title: "Files list problem with dpkg install"
date: 2011-07-06
forum: General Help
---

### Post by castalla on 2011-07-06
Are there any wizards out there who can help with this?

> login as: user
user@192.168.0.134's password:
Linux SmartQ 2.6.28 #907 PREEMPT Fri Mar 12 16:27:10 CST 2010 armv6l

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

0 packages can be updated.
0 updates are security updates.

user@SmartQ:~$ sudo dpkg -i --no-act squeezeboxserver_7.5.5~32569_all.deb
Selecting previously deselected package squeezeboxserver.
(Reading database ... 5%
dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `samba-common-bin': Input/output error
user@SmartQ:~$


Both the two referenced packages are installed and up-to-date.

Newbie advice please!

---

