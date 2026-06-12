---
title: "Boot up failure...what now?"
date: 2010-02-06
forum: General Help
---

### Post by bpont on 2010-02-06
```
Mount: mounting /dev/disk/by-uuid/[uuid]/ on /root
Failed: invalid argument
Mount: mounting /sys on /root/sys failed. No such file or directory.
Mount: mounting /dev on /root/dev failed. No such file or directory.
Mount: mounting /sys on /root/sys failed. No such file or directory.
Mount: mounting /proc on /root/proc failed. No such file or directory. 
Target file system doesn't have /sbin/init
No init found. Try passing init=bootarg.


Busybox v1.13.3(ubuntu1:1.13.3-1ubuntu7) built-in (ash)

Enter 'help' for a list of built-in commands.

(initramfs)_
```

I"m not sure what caused this to happen or how to troubleshoot / solve this issue.

Accessing the file system from a rescue disk may not be an option, since the installation lives on a virtualbox virtual disk.

Any skillful advice is very welcomed.  I'd like to get this system back.

---

### Post by quixote on 2010-02-07
It shouldn't be trying to mount / on /root.  That's weird.  Are you using karmic, ie grub2, or an earlier version with old grub?  If it's the old version, check /boot/grub/menu.lst and post the four or five lines that specify the ubuntu boot location.  They'll look something like this:```
title		Ubuntu 9.04, kernel 2.6.29-02062904-generic
uuid		78b9d228-030a-431b-b1ce-49a7b3e32101
kernel		/boot/vmlinuz-2.6.29-02062904-generic root=UUID=78b9d228-030a-431b-b1ce-49a7b3e32101 ro quiet splash 
initrd		/boot/initrd.img-2.6.29-02062904-generic
quiet
```

In grub2, I don't remember exactly where that info is.  I'll have to look it up.  

I don't remember, from my one time of struggling with initramfs, just how much it will let you do.  I don't see much out on the web either.  So far, this is the only somewhat useful-looking page: [http://en.gentoo-wiki.com/wiki/Initramfs#Rescue_shell](http://en.gentoo-wiki.com/wiki/Initramfs#Rescue_shell).

In the case of a virtual machine, it usually occupies all of its one virtual drive, which vbox usually calls "sda" or the like. So you can dispense with the uuid stuff if you want.  "/dev/sda1" or whatever it should be on your system, works fine.

---

