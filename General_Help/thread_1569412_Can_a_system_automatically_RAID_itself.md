---
title: "Can a system automatically RAID itself?"
date: 2010-09-06
forum: General Help
---

### Post by Mhoram on 2010-09-06
(This is such a weird question I wasn't even sure where to ask it.  Here goes.)

When I installed this system (Xubuntu 9.04 x64) several months ago, I had two identical SATA hard drives, but I didn't do a RAID1 mirror then because I didn't want to wipe out my old OS (FreeBSD) on the second drive in case I needed to retrieve something from it.  So I installed Xubuntu on the first drive (sda) and for all that time, the second drive (sdb) has been running but unused, and fdisk showed that the FreeBSD partition was still there.

A couple weeks ago, my separate backup server failed, so as a short-term backup I did a 'dd if=/dev/sda of=/dev/sdb' to make an exact copy of my Xubuntu install on drive A upon drive B (the former FreeBSD drive), then mounted /dev/sdb1 on /mnt to make sure it worked successfully.  So far so good, but I still didn't set up any RAID stuff.  

Several days later, I needed to reboot because of a security upgrade, and when I logged out, the GUI froze up.  Thinking not too much of it, I restarted the system, and it came up fine.  But the next day, I discovered that I was missing several days worth of email and recent files.  In fact, everything had been reverted back to a state from several days earlier --- I think from the day I copied the first drive to the second one.  Files I created in the interim were gone, and files I deleted in the interim were back.  It was as if the first drive was 'restored' from the second one without my knowledge.

Doing some testing now, I find that if I create a new file on /dev/sda1 and then mount /dev/sdb1, the file also exists on sdb1.  It's as if they're acting as a RAID1 mirror, without my telling it to do so.  Could it just decide to do RAID1 because it sees there are two identically partitioned drives?  That seems dangerous.  And if they were really in a RAID mirror, why would it let me mount them separately?  It's very strange.

Any ideas?  I don't mind if it's suddenly decided to do RAID, but I want to make sure it's not going to 'restore' a more current filesystem from an older one again, if that's indeed what happened.

Thanks.

---

### Post by ronparent on 2010-09-06
Off hand I would say it is not likely that two drives could raid themselves. A software raid definitely no. A fakeraid only if the drives are raided by the MB raid bios. Try typing the following in a terminal: sudo blkid

If you have a raid the partitions would be identified as such as a block devices. 

I think it is more likely that when you copied your drive, the partitions were copied verbatim including the uuid's. In which case, since grub searches for the boot drive by uuid you never know which one may be booting (the original or the copy). You might have to unplug the copy to protect your system from schizoid behavior.:p

---

### Post by Mhoram on 2010-09-06
Looks like you nailed it; blkid reports identical UUIDs.  So I guess when the kernel writes a file to /dev/sda1, it actually writes it to the device with the corresponding UUID, and since there are two of them, it writes it to both of them.  Yikes.

One thing still doesn't make sense, though:  When I discovered that a bunch of my files were missing, I wondered if the drives had gotten switched on boot somehow, so I mounted the 'second' drive, and the missing files weren't there either.  It seems like if grub just got the partitions switched, *one* of them should have had the files I created over those several days.  But maybe that *does* make sense: if data is being written to both drives at a low level (like at the block level), changes to enough index blocks would soon wipe out links to files too.

Thanks very much!

---

### Post by ronparent on 2010-09-07
It almost sounds like copying a partition to another drive is one way of creating an automatic backup!!! I wouldn't rely on it however. Its probably flaky at best.

Glad to hear that issue is cleared up.

---

