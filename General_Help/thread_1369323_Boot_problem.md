---
title: "Boot problem"
date: 2009-12-31
forum: General Help
---

### Post by Tribulation on 2009-12-31
I just installed Ubuntu 9.10 on my mother's computer for her and ran update manager for the first time. While it was updating it told me that I'd have to restart to finish, so I chose the restart option. While it was loading it hung on the white Ubuntu symbol right before the splash page. After staying there for some time the screen went black and all I could see was

```
 fsck from util-linux-ng 2.16
[   3.575240] Adding 6032368k swap on /dev/sda5.   Priority:-1 extents:1 across: 6032368k
/dev/sda1: clean, 151614/9396224 files, 1245533/37553937 blocks
init: udevtrigger main process (549) terminated with status 1
init: udevtrigger post-stop process (551) terminated with status 1
init: udevtrigger main process (548) killed by TERM signal
init: networking main process (554) terminated with status 1
```


EDIT: I've rebooted twice since then and now I only get

```
fsck from util-linux-ng 2.16
[   3.575240] Adding 6032368k swap on /dev/sda5.   Priority:-1 extents:1 across: 6032368k
/dev/sda1: clean, 151614/9396224 files, 1245533/37553937 blocks
```

Also, I'm not sure if this is any help but when I restarted before it just booted into Ubuntu, but ever since the problem started showing up, it's been booting into GRUB.

---

### Post by isaacf on 2010-01-27
I can confirm the existence of this problem. Something very similar is happening to me with 9.10 on my Lenovo Thinkpad sl510.

---

### Post by isaacf on 2010-01-27
After reading through this thread: [http://newyork.ubuntuforums.org/showthread.php?t=1318593](http://newyork.ubuntuforums.org/showthread.php?t=1318593)

I edited /etc/fstab as described here: [http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html](http://creativeinstantia.blogspot.com/2009/11/upgrade-to-karmic-koala-kubuntu-910.html)

and so far things seem to be going well.

---

### Post by cesium62 on 2011-04-09
Isaac's posting appears to be completely unrelated to this thread.  I assume he posted to the wrong thread.  The link he references discusses problems with fstab possibly associated with a long running fsck.  The fact that he can edit fstab indicates his kernel is not hung after displaying the udevtrigger error message.

---

