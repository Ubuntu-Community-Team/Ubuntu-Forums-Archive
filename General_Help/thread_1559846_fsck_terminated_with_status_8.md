---
title: "fsck terminated with status 8"
date: 2010-08-24
forum: General Help
---

### Post by mendhak on 2010-08-24
This morning, I booted up my laptop and the boot sequence got stuck at the boot splash screen (plymouth).  

I did an esc and I saw a failure message, the error I remember in my panic mode is: 

fsck terminated with status 8

I rebooted, got the same message.  Rebooted again and this time, to my relief, it worked.

1) What happened, should I be concerned?  Not sure why it worked after 2 reboots.
2) Is there a possibility this could happen again?
3) Are there any boot log files I could look at?
4) Is there anything I can do to fix this? Or a check of some sort?

I'm using Ubuntu 10.04 on a Dell Studio 1535 laptop.  No dual boot.  The disk is partitioned and I've got my /home folder on the other partition for situations like this, but it still makes me worry :D

---

### Post by mendhak on 2010-08-25
So after some searching, I see that there's a /var/log folder.  It has a few files of interest, namely:

syslog
messages
boot

However, the boot log file can only be filled if you explicitly enable boot logging by opening up /etc/default/bootlogd and setting BOOTLOGD_ENABLE=yes.  

(un?)fortunately, the problem hasn't happened again on subsequent boots so I can leave this for later. Can fsck only be run by using a livecd?

---

### Post by varunendra on 2010-08-25
> **mendhak said:**
> Can fsck only be run by using a livecd?

fsck needs the drive it is going to scan be locked, so yes, to scan / (or /boot), you'll have to use an external OS like a live cd. For /home (if it is on a separate partition), I think you can fsck while logging in as root.

The point is, 'the drive should/can not be in use while performing fsck'.

---

