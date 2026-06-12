---
title: "unable to boot: udevd not found after removing"
date: 2006-06-16
forum: General Help
---

### Post by mtron on 2006-06-16
Hi guys! came up with a strange problem yesterday, now i'm out of ideas. i installed dapper some months ago. was working smoothly till yesterday, when i decided to remove usplash & upgraded to the new 2.6.15-25 kernel

did remove usplash while working with the old kernel  with apt-get purge all, seemed to work ok, when i wanted to restart my PC 2day, i got following error (on both, recovery and usual boot):

Uncompressing Linux ... ok, booting the kernel
/scripts/init-premount/udev: 24: /sbin/udevd: not found
/scripts/local-top/udev: 30: /sbin/udevplug: not found

that's all, nothing more is happening.

Did sb come across this problem or know what to do (without a reinstall if possible)?

Edit: might have something to do with the kernel upgrade, discussed in the thread:
[http://www.ubuntuforums.org/showthread.php?p=1144822](http://www.ubuntuforums.org/showthread.php?p=1144822)

cheers

---

### Post by Rui Pais on 2006-06-16
Hi,
are you sure you not purge by mistake typing udev instead of usplash?
(you could check your .bash_history file...)

Didn't you have another kernel to boot, to ensure that it's a new kernel problem or a broken udev? 
Or launch from a live cd, mount your ubuntu and check if you got: 
> /etc/init.d/udev
/etc/rcS.d/S*udev
/etc/udev/*
/sbin/udev*

---

### Post by mtron on 2006-06-16
yea, took another kernel and removed the new kernel, will wait with the update a bit ;)

---

