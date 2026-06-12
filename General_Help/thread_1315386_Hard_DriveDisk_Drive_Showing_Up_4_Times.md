---
title: "Hard Drive/Disk Drive Showing Up 4 Times"
date: 2009-11-05
forum: General Help
---

### Post by Spazmunki13 on 2009-11-05
Hello all, I installed Ubuntu last night and I noticed in the Disk Utility that my hard drive shows up 4 times!

This is kind of what the screen looks like:

160 GB Hard Disk
--
--- MBR Partition Table
---- 160 GB Free
----- Unallocated Space

154 GB Hard Disk
--
--- Not Partitioned
---- 154 GB Filesystem
----- Linux Ext4 (version 1.0)

6.2 GB Hard Disk
--
--- Not Partitioned
---- 6.2 GB Swap Space
----- 6.2 GB

160 GB Hard Disk
 -- ATA WDC WD1600JS-60NCB1
--- MBR Partition Table
 ---- 160 GB Free
 ----- Unallocated Space

160 GB Hard Disk
-- ATA WDC WD1600JS-60NCB1
--- MBR Partition Table
---- 160 GB Free
----- Unallocated Space

I'd like to know how to remove those extra entries but I'm not sure how to and if it would affect the system.

Thanks in advance.

Matt

---

### Post by dvlchd3 on 2009-11-05
Does fdisk show the same entries?

```

sudo fdisk -l

```

---

### Post by Spazmunki13 on 2009-11-05
I think it's showing two of them now not sure...
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3f6117

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18705   150247881   83  Linux
/dev/sda2           18706       19456     6032407+   5  Extended
/dev/sda5           18706       19456     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3f6117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18705   150247881   83  Linux
/dev/sdb2           18706       19456     6032407+   5  Extended
/dev/sdb5           18706       19456     6032376   82  Linux swap / Solaris

---

### Post by P4man on 2009-11-05
Can you post a screengrab?

Easy way to post screenshot in under 10 seconds: 
-install **shutter** from the software centre. Run it from accessories

-Make a screenshot using the third option "select a window" 
-Click on the palimpsest window you want to show us
-After making the shot right click the thumbnail > upload > pick any provider you want
-click the "copy this code" next to the style of your choice
-paste in your post.

---

### Post by Spazmunki13 on 2009-11-05
[[img]http://www.ubuntu-pics.de/thumb/29866/screenshot_002_AeiYn8.png[/img]](http://www.ubuntu-pics.de/bild/29866/screenshot_002_AeiYn8.png)

This is it right?

---

### Post by P4man on 2009-11-05
yep that works. And that looks pretty screwed up indeed. Palimpsest seems quite confused. Id just ignore it for now, file a bug report against palimpsest, but it should  not affect you in any other way. Your fdisk output looks quite normal so I doubt there is a deeper underlying problem.

---

### Post by Spazmunki13 on 2009-11-05
Alright, thank you very much. :)

---

