---
title: "File explorer stops responding when transferring from NTFS to Ext4"
date: 2010-09-29
forum: General Help
---

### Post by Auax on 2010-09-29
So I've got a 500gb ext4 formatted drive I use for backup, and I'm trying to save my personal files from my laptop's hard drive (the laptop power supply just died), but whenever I try to copy+paste something from the NTFS laptop drive to the ext4 drive, nautilus freezes up, and suddenly both of my CPU cores hit 100% and Ubuntu is using 1.6GB of RAM, from like 200MB when it's idle.

I'm using 10.04
Pentium D 2.4Ghz Dual
2GB RAM

The laptop drive is a 5000RPM 250GB Sata, NTFS partition is 125GB
The backup drive is a 7200RPM 500GB Sata, ext4 partition is 500GB

---

### Post by 7h3d4rk0n3 on 2010-09-29
Have you tried to copy small portions of it at a time and see if it freezes that way? Also, if it freezes and you just let it sit, does it eventually finish? Sometimes it will freeze while copying for me, but will recover after it is done.

---

### Post by Auax on 2010-09-29
> **7h3d4rk0n3 said:**
> Have you tried to copy small portions of it at a time and see if it freezes that way? Also, if it freezes and you just let it sit, does it eventually finish? Sometimes it will freeze while copying for me, but will recover after it is done.I have, I tried waiting while copying a 25MB folder, and ended up terminating the process after 40 minutes.

---

### Post by 7h3d4rk0n3 on 2010-09-29
First thing I would do is to check for updates to Nautilus.

---

### Post by Auax on 2010-09-29
Will do so, and re try.

---

### Post by Auax on 2010-09-29
Ok, so I've updated, and come across some strange stuff when troubleshooting. Transfers between the other NTFS partition on the same drive and my ext4 disc work fine. The Partition in question isn't always recognized as an NTFS partition, sometimes it just says "fuseblk" and the name is some hexidecimal digits. I can explore the filetree fine, but any time i try to transfer something from it, nautilus freezes and has to be force quit.

An fsck came back clean.

---

### Post by 7h3d4rk0n3 on 2010-09-29
Are you able to xfer from the HEX partition to another NTFS partition?

---

### Post by Auax on 2010-09-29
> **7h3d4rk0n3 said:**
> Are you able to xfer from the HEX partition to another NTFS partition?

Yep, it works just fine.

---

### Post by Auax on 2010-09-30
If it helps, this is what the title looks like for the problem partition

[img]http://imgur.com/wNjSI.png[/img]

All other partitions have their standard volume label set in Windows 7

---

### Post by Auax on 2010-09-30
21-hour bump.

---

### Post by Auax on 2010-09-30
Any help would be awesome, anything at all. I'm losing money every hour I don't have a working windows machine.

---

### Post by Auax on 2010-10-01
And transferring between the NTFS partitions no longer works.

---

### Post by 7h3d4rk0n3 on 2010-10-01
Hm... only other thing I can really think of is to use a 3rd party file explorer and see if you can see the partitions and copy back and forth that way.  If that doesn't work, I would recommend reformatting the NTFS partition that is giving you trouble to a FAT partition and see if that helps at all.

---

### Post by Auax on 2010-10-01
I actually just got tired of it and booted the Windows 7 drive on this computer and let it install the drivers it needs to run here. Now if I can find out how to write to ext4 from W7, I'll be golden.

---

### Post by 7h3d4rk0n3 on 2010-10-01
Good luck with that, all the file managers that I have tried have not worked very well.

---

### Post by Auax on 2010-10-01
You're right, i can't find any that work anyways.

Ugh.

---

