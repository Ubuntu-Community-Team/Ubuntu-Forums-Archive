---
title: "Help! My / directory is borked!"
date: 2010-07-03
forum: General Help
---

### Post by JKyleOKC on 2010-07-03
I urgently need expert assistance. During a cold-start reboot, something corrupted my / directory making it impossible to access much of anything.

I was able to log into a recovery console and do "ls /" which shows most of the critical directories although "media" is missing. However attempting to "ls /home" gets the "no such file or directory" error message, as do attempts to ls most of the others. Doing "ls -l /" gets one item listed, followed by a single record out of /var/log/syslog, then nothing at all.

Attempting a normal login (I've disabled the quiet and splash  options, so I see all the startup messages) gets to doing fsck on the swap partition, and that stalls out at 14% complete. The fsck on the root partition completed okay, apparently.

This machine is my router, firewall, FTP server, and also hosts VirtualBox VMs that contain all of my customer support tools. The VMs themselves are partially backed up on another box, fortunately, but it took me a couple of months to get the failed box configured properly so if possible I need to recover it. For lack of space, I've never been able to do a full backup of it -- and permissions have foiled portions of all my other backup attempts on it.

Complicating matters is the fact that I have a moderately large data recovery job scheduled to arrive this evening (July 3) to be done while the customer's business is shut down for the holiday. Without the FTP server I'm unable to receive the files, which will total from 100 to 200 MB in all.

Is it likely that testdisk may be able to rebuild the borked main root directory, if run from a live CD?

The system is Hardy LTS 8.04.4, with 3 GB of RAM and a 250 GB SATA drive. I'm posting this from my WinXP laptop, which doesn't get along with my LAN so connects from a different router than the one that's down.

---

### Post by cogier on 2010-07-03
There is a lot there but if the following is possible please try it.

If after getting all the (error) messages about **fsck** or anything else you end up at a terminal prompt type **fsck** and [Enter].

It may seem that this is not necessary as you have seen fsck report errors - BUT when it did that the dive was mounted. Now run the command with the drive **unmounted**.

I can't promise anything but here's hoping. Then you will need to reboot.

---

### Post by JKyleOKC on 2010-07-03
I'll try that later; my immediate fix is to replace the drive, reinstall what I need most, and recover from backups...

Thanks for the suggestion; that had not occurred to me!

---

### Post by JKyleOKC on 2010-07-04
The immediate emergency is mostly over. I put in a new 500 GB drive, re-installed Hardy, plus 257 updates and then the various server packages (postfix, proftpd, openssh, etc). Restored the entire /etc directory from yesterday's full backup of it and that took care of most of the configuration although I did have to manually edit /etc/fstab because the drive identities changed. Installed VirtualBox next, and began the 3-hour process of restoring all the VMs from a 10-day-old full backup of them. While all this was going on I got in touch with the customer and postponed the upload of her data until tomorrow afternoon, so the major pressure is off.

I'll be trying to salvage all that I can from the old 260-GB drive; does anyone know whether I can fsck it via a USB patch cable, rather than having to open the box up and install it again?

---

