---
title: "sudo vs root"
date: 2011-10-10
forum: General Help
---

### Post by qiucx on 2011-10-10
I use ubuntu 10.0.4 and fail to use sudo caused by "sudo: must be setuid root".
And my root role is not start too. I tried to modify /etc/gdm/gdm.conf to allow the root login, however, the file is not found. I google the way to solve it, and find it can be done by using "single user mode", unfortunately, my ubuntu is under vmware and i do not know how to entry this mode, can anybody know how to solve it? thanks.

---

### Post by snowpine on 2011-10-10
Welcome to the forums! Please read this Sticky at the top of the Security forum:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Anything you need to do can probably be done with 'sudo' so please post more details about the problem. We'll try to help. :)

---

### Post by vajorie on 2011-10-10
> **qiucx said:**
> I use ubuntu 10.0.4 and fail to use sudo caused by "sudo: must be setuid root".
...
find it can be done by using "single user mode", unfortunately, my ubuntu is under vmware and i do not know how to entry this mode, can anybody know how to solve it? thanks.

Reboot your vmware instance and as it is booting (at the very start), hold down the SHIFT key (and if that doesn't work, hold down the ESC key). ([source]("https://help.ubuntu.com/community/Grub2#GRUB_vs_GRUB_2"))

There, choose the recovery mode (or something like that --I forgot its name), which will give you a root prompt (single user mode). You can then solve the suid problem you are getting --though I would also investigate why this happened in the first place).

---

