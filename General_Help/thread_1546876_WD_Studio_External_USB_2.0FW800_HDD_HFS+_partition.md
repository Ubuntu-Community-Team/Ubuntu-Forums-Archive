---
title: "WD Studio External USB 2.0/FW800 HDD HFS+ partition mounts as read-only"
date: 2010-08-06
forum: General Help
---

### Post by OrangeVixen on 2010-08-06
I just got a new WD Studio External USB 2.0/FW800 hard disk drive, it is formatted to HFS+ with Journaling (hfsplus) and I use it for both an iMAC and a PC/Linux. The problem is that on my PC (Linux - Ubuntu 9.10) there is always some kind of read-only error whenever I try to edit, create, delete anything on it.

I tried it on my iMAC and I'm able to read and write on it with no problem.

The mount command on Linux gives me:

/dev/sdc3 on /media/My Passport type hfsplus (rw,nosuid,nodev,uhelper=devkit)

Clearly indicating that it ("My Passport" on /dev/sdc3) is mounted as "rw" (read and write, not read-only).

I tried connecting it via Firewire 800 and USB 2.0 and both give me the same results.

I also tried fixing it in my iMAC using Disk Utility but it reports on problem and I clearly safely "Ejected" it before unplugging it from my iMAC.

---

### Post by OrangeVixen on 2010-08-06
Update, I read a few posts that HFS Journaling needs to be disabled in Mac OS. I went to Disk Utility on my iMac and there was no option to disable Journaling, so I reformatted the HDD to HFS Extended (without journaling).

Then set the permissions to read and write for everyone.

The wierd part happens, I safely unmounted it on my iMac and then moved it to my PC, then sometimes it mounts as read and write and some times it mounts it as read only. I have to try a few times, unmount it and bring it back to my iMAC and try to fix it (Disk Utility always says it is OK every time).

Is there any other posibility for this discrepency?

---

