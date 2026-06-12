---
title: "can't mount /etc/fstab"
date: 2010-01-16
forum: General Help
---

### Post by afderrick on 2010-01-16
So I was playing on my computer like normal.  F-spot froze the system up and since Ubuntu killed the ability to restart X with the ctrl alt del backspace I had to reboot the machine.  When I turned it back on after it was over I received a message after posts saying it could not mount the /etc/fstab file.  I have never edited the /etc/fstab file so there should be nothing wrong with it.  Am I have hard drive errors or has anyone else seen a problem like this?  I cannot find much help online since it seems most people manually messed up there fstab.

---

### Post by kellemes on 2010-01-16
> **afderrick said:**
> So I was playing on my computer like normal.  F-spot froze the system up and since Ubuntu killed the ability to restart X with the ctrl alt del backspace I had to reboot the machine.  When I turned it back on after it was over I received a message after posts saying it could not mount the /etc/fstab file.  I have never edited the /etc/fstab file so there should be nothing wrong with it.  Am I have hard drive errors or has anyone else seen a problem like this?  I cannot find much help online since it seems most people manually messed up there fstab.

"can't mount /etc/fstab" is the exact message?
Rings no bell..

---

### Post by sisco311 on 2010-01-16
Boot a LIVE CD and check the partitions for errors via GParted, or from a terminal:

```

sudo umount /dev/sdXY
sudo e2fsck -C0 -f -v /dev/sdXY
```
replace sdaXY with the actual device name (i.e. /dev/sda1).
```
sudo fdisk -l
```lists the partistions.

---

### Post by afderrick on 2010-01-16
I have rebooted and it came back up after performing a file system check.  So I'm not exactly sure what happened.  But yeah, unable to mount or find /etc/fstab was the message I received.  It worried me when I was unable to find anything searching the Internet as well.

---

### Post by Iowan on 2010-01-16
> **afderrick said:**
>   But yeah, unable to mount or [COLOR="Red"]find[/COLOR] /etc/fstab was the message I received.  Have you verified that the file still exists?

---

### Post by afderrick on 2010-01-16
Yeah, after I went into recovery mode and hit ctrl+D it restarted it again and found it without a problem.  So I'm not entirely sure what is up.  It did perform a file system check as well at that time

---

### Post by n0dix on 2010-01-16
> **afderrick said:**
> So I was playing on my computer like normal.  F-spot froze the system up and since Ubuntu killed the ability to restart X with the ctrl alt del backspace I had to reboot the machine.  When I turned it back on after it was over I received a message after posts saying it could not mount the /etc/fstab file.  I have never edited the /etc/fstab file so there should be nothing wrong with it.  Am I have hard drive errors or has anyone else seen a problem like this?  I cannot find much help online since it seems most people manually messed up there fstab.

The Ctrl-Backspace utility has you to add manually. It is disable.

---

