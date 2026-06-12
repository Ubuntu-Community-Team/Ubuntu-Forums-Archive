---
title: "Can't run konqueror as root"
date: 2006-03-17
forum: General Help
---

### Post by Gnu32 on 2006-03-17
I'm trying to run konqueror as root by modifying the shortcut in the panel so it runs it as root. I put in the password as required and it sits in the taskbar with the hourglass animation for 20 seconds, and then disappears. I've kept trying this but nothing works.

Also, the service for handling root access seems faulty, especially in system prefrences where 'Administrator mode' doesn't work (I put in my password, but everything is still greyed out)

Any solutions?
Cheers

Edit: I've done what my fellow newbies tend to do when they think they know what they're doing, and made Kubuntu unbootable. What i did was i moved my account to the root group and gave root a password through users and groups

And now i'm sitting here in the BusyBox prompt after:
'lseek: invalid argument
<usage settings here>
mount: cannot read /etc/fstab: No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: NSFoD
mount: Mounting /dev on /root/dev failed: NSFoD
Target filesystem doesn't have /sbin/init'

And before the busybox waiting prompt:
/bin/sh: can't access tty: job control turned off

Fixable through busybox? >_<

---

### Post by FizDev on 2006-03-17
Maybe you could try to open a terminal and type 
```
sudo konqueror
```
or whatever the konqueror bin is... :confused:

---

### Post by Aewheros on 2006-03-17
Never use *sudo *to run graphical applications, though. Use *gksudo*, instead.
Using *sudo *can prevent you from logging in until fixed.

---

### Post by aysiu on 2006-03-17
For Konqueror, your best bet is to create a launcher with the command ```
kdesu konqueror
```

---

### Post by Gnu32 on 2006-03-17
Cheers to both of you
Any ideas on the startup problem though?

---

