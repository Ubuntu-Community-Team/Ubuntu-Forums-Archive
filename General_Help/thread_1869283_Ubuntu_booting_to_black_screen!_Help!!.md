---
title: "Ubuntu booting to black screen! Help!!"
date: 2011-10-25
forum: General Help
---

### Post by maxmccabe on 2011-10-25
Hi there,

I'm running 11.10 on an '07 macbook. I rebooted and now when Ubuntu start the loading splash screen appears for a second then the goes black - the computer is still running but is completely unresponsive.

I changed the synaptics touch pad driver in /usr/X11/xorg.conf before the install but i don't see how this would stop it loading?

The only other change I made was to increase the resolution during start up, although I have rebooted it successfully after this change.

Please any help would be massively appreciated.

---

### Post by maxmccabe on 2011-10-25
The screen now just says:

stdin: I/0 error
mount: mounting /dev/loop0 on //filesystem.squashfs fail: No such device

can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

udevde[82]: worker [184] unexpectedly return with status 0x0100

udeve[82]: worker [184] failed while handling '/devices/virtual/block/loop0

---

### Post by tomgnu on 2011-10-25
may be of help.

[http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html](http://thegreyhats.blogspot.com/2011/10/ubuntu-1110-upgrade-black-screen-cant.html)

---

