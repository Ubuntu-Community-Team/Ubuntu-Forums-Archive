---
title: "/ as read only"
date: 2012-02-26
forum: General Help
---

### Post by shashanksingh on 2012-02-26
It started when I installed wine and then tried to install counter strike.

Suddenly nautilus started showing folders as read only, even my home folder.

On reboot,it first checks the disk each time for errors and shows some of logs that it cannot create any file in the file system partition. Then it hangs on the last line saying 

```

* starting daemon Winbind

```

I thought some problem with wine, so from tty1 I tried to sudo-apt-get purge wine*

It said it cannot access the lock, read-only

I booted from 10.04 cd, and checked the fstab. It said error-remount-ro for the system partition.
I changed that to defaults, thinking maybe that may help.

But its the same

Do help, coz I'm in a bit crisis here...

---

### Post by mcduck on 2012-02-26
If the drive is  mounted as read-only because it contains errors, the solution of course isn't to disable this behaviour but to try to *fix the errors*. ;)

Try running fsck on the drive, either from recovery shell or from a live-CD. And if that doesn't help, use the live-CD to check the drive's SMART status.

...once you get the filesystem errors sorted out, it will automatically get mounted in read/write mode again. The reason for read-only mode in case of errors is simply to protect the filesystem from any further damage.

---

### Post by shashanksingh on 2012-02-28
> **mcduck said:**
> If the drive is  mounted as read-only because it contains errors, the solution of course isn't to disable this behaviour but to try to *fix the errors*. ;)

Try running fsck on the drive, either from recovery shell or from a live-CD. And if that doesn't help, use the live-CD to check the drive's SMART status.

...once you get the filesystem errors sorted out, it will automatically get mounted in read/write mode again. The reason for read-only mode in case of errors is simply to protect the filesystem from any further damage.


fsck from another bootable CD showed me a lot of errors for about half-an-hour and then asked me to press f to fix some errors at the end. Still didnt help, the condition was the same after that. I did what most other do, format and fresh install :-(

---

