---
title: "Having Trouble Resizing Partitions"
date: 2012-02-22
forum: General Help
---

### Post by maffewwww on 2012-02-22
I recently wanted to try Ubuntu as a dual-boot along side WIndows 7 but ended up ruining Windows 7 and now I just have Ubuntu 11.10 installed, so I'm VERY new to Ubuntu. I'd like to make a partition so I can re-install Windows but all my hard drive space is taken up by Ubuntu's ext4 partition (Nearly 600GB) I'd like to shrink this down so I can format an NTFS partition for W7 but I can't unmount the ext4, resize, or edit it at all. Please help! I'm using GParted. How can I get space for Windows!

I did the fdisk -l thing in a terminal window and this is what I got: 
(I don't know how to show it in a window, Sorry :\ )

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003dcb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1234020351   617009152   83  Linux
/dev/sda2      1234022398  1250263039     8120321    5  Extended
/dev/sda5      1234022400  1250263039     8120320   82  Linux swap / Solaris

---

### Post by Cheesemill on 2012-02-22
You cannot resize a partition if it is currently in use, which is the case if you're using Gparted from a running system. You need to boot from the Live CD and run Gparted from that instead.

If you are pasting code in the forum just surround it with  CODE tags to get the text in a nicely formatted window (or select the text and hit the # icon) :)

---

### Post by maffewwww on 2012-02-22
Thank you very much :D I'll try that right now and come back to confirm.

---

### Post by maffewwww on 2012-02-23
It worked! Thank you so much for your quick reply. :)

---

