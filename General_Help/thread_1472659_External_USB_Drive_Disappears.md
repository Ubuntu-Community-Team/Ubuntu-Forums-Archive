---
title: "External USB Drive Disappears"
date: 2010-05-04
forum: General Help
---

### Post by concord on 2010-05-04
Ubuntu 10.4 x86
External USB Panasonic OneTouch 4 HDD formatted Ext2

After rebooting the computer the USB external HDD I use for backup appears and is accessible at /media/OneTouch 4

A few minutes later I check and it's unmounted itself (apparently) because it's no longer there. 

Restart the computer and it appears for a while once again, then disappears.

---

### Post by nachovidal on 2010-05-10
Same here! Please help.

---

### Post by huarewe on 2010-07-18
Same problem here, I've noticed it has been a bug on several versions of ubuntu and other linux flavors, but I couldn't find a real solution, though one person mentioned trying to disable usb 2.0, thus making your external drive reallly slow...

---

### Post by huarewe on 2010-07-18
Just to follow up, its not that it UN mounts perse, its just that it stops reading it and thus the files appear to disappear from the mount dir. 

If you do a df -h, it still shows the device but you can't communicate iwth it, I have to physically unplug the drive and remount it manually. For example, in the last two days I've done it twice, so my output looks like this: 

/dev/sdb1             466G  240G  227G  52% /media/lacie
/dev/sdc1             466G  240G  227G  52% /media/lacie
/dev/sdd1             466G  240G  227G  52% /media/lacie


sdb, sdc, and sdd are the same drive.... Its just that once it 'dies' under one device name, i have to remount it under a new device name after unplugging/replugging

When the drive "disappears" dmesg spits out a series of these messages:

[343125.212263] FAT: Directory bread(block 119340) failed

I've heard some people mention this can happen when it is not in use, but I actualyl physically watched the device go offline this time, and it was most certainly in use (by a backup program). 

Finally, to be sure, the drive is not damaged. 

And again, googling revealed a lot of bug reports and complaints about this from older versions of ubuntu, but I couldn't find a solution, so any help would be greatly appreciated.

---

### Post by digitalb0y on 2010-10-17
I too have this issue even with the last update I've even tried mounting it with the UID name same issue. It changes device names about every 24 hours!!

---

### Post by bjsiders on 2011-01-30
Mark me down.  I bought a 2 TB drive for streaming media for our Dune player and it will sit there happily for weeks on end, so long as nobody is using it.  Once you do a few read/writes, it vanished from /dev but the mount point still shows up in 'df'.  It's also not listed in /proc/partitions.

No clue, but this is highly annoying, it renders my entire streaming media set up worthless unless I want to back all this data up and install another OS.

---

