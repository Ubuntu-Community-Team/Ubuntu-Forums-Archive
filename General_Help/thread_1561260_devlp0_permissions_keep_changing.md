---
title: "/dev/lp0 permissions keep changing"
date: 2010-08-26
forum: General Help
---

### Post by mthalis on 2010-08-26
The problem is whenever we reboot the system the permissions of /
dev/lp0 (line printer) is changing. So every time we are changing the /
dev/lp0 permissions through root using chmod 777 /dev/lp0

Is there any smooth solution for this?

Why the /dev/lp0 permissions are changed with every reboot?

Please help me I'm using ubuntu 10.04 and Epson 300+2

---

### Post by sisco311 on 2010-08-26
[Device nodes]("http://en.wikipedia.org/wiki//dev") are created during the bootup by udev. 

Usually the lp group has read/write permissions for /dev/lp*. So, if you want to allow a user to use the printer, simply add it to the lp group:
```
sudo gpasswd -a **username** lp
```

If, for whatever reason, you want to change the permissions of /dev/lp*, you have to write a udev rule.

[http://wiki.archlinux.org/index.php/Udev](http://wiki.archlinux.org/index.php/Udev)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by mthalis on 2010-08-26
$who gave below output 

> 
prime    tty7         2010-08-27 09:04 (:0)
prime    pts/0        2010-08-27 09:13 (:0.0)


After that I used your command 
> sudo gpasswd -a prime lp

But after restarting machine **lpo permission gone**

$ls -l gave this 
 > crw-rw---- 1 root lp 6, 0 2010-08-27 09:03 lp0

How can I solve this problem

---

### Post by sisco311 on 2010-08-27
What problem exactly are you having? 

The lp group has read/write permission for /dev/lp0 and your user is in the group. You should be able to use the printer.

---

### Post by mthalis on 2010-09-01
Sorry for the late reply. It worked now. I used > sudo gpasswd -a username lp Thank **sisco311**

---

