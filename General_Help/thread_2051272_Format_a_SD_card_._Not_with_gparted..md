---
title: "Format a SD card . Not with gparted."
date: 2012-09-01
forum: General Help
---

### Post by irv on 2012-09-01
I have a 32gig SD card that I keep in my card slot in my laptop. Today I was using Unetbooten to make a USB boot drive for an install, and I inadvertently screwed up the SD card. Well I went to format it with gparted, and before I did that I was going to try to recover some files from it. After letting it run for hours, I decided to just format it and forget about the files. So I stopped the recovery process, but now every time I put the card in the slot and run gparted it just goes back to searching partitions. Again I just let it run for hours and nothing seems to be happening.
Now for the question. Is there any way I can just format this card not using gparted?

---

### Post by dino99 on 2012-09-01
[http://www.ehow.com/how_6080534_format-sd-card-ubuntu.html](http://www.ehow.com/how_6080534_format-sd-card-ubuntu.html)

---

### Post by irv on 2012-09-01
My problem is it is always busy because it can't read it so it doesn't mount or unmount. Here is the command I use and the message I get:
```
irv@irv-Inspiron-1521:/dev$ sudo mkdosfs -F 32 -v mmcblk0p1
[sudo] password for irv: 
mkdosfs 3.0.12 (29 Oct 2011)
mkdosfs: unable to open mmcblk0p1: Device or resource busy

```
mmcblk0p1 is the name for the SD card.
When I try to mount it in file manager this is what I get.
[ATTACH]223509[/ATTACH]
And like I said if I try anything with gparted, it just keeps trying to scan the partitions.

---

### Post by irv on 2012-09-01
OK I am going to mark this one solved.
Here is what I did to fix this problem.
I ran Unetbootin again and tried to create another boot device on the SD card, It said it didn't have enough room (SD full) so I said to ignore and I had to keep clicking "No" until it was done. Then I could mount and unmount it. At that point I did this again and here is the results.
```
irv@irv-Inspiron-1521:/dev$ sudo mkdosfs -F 32 -v mmcblk0p1
[sudo] password for irv: 
mkdosfs 3.0.12 (29 Oct 2011)
mmcblk0p1 has 4 heads and 16 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 62325760 sectors;
file system has 2 32-bit FATs and 32 sectors per cluster.
FAT size is 15232 sectors, and provides 1946727 clusters.
There are 32 reserved sectors.
Volume ID is 929795fc, no volume label.
```
Here are the properties of the SD Card.
[ATTACH]223516[/ATTACH]
I lost the files on the card, but I had them backed up elsewhere.

---

