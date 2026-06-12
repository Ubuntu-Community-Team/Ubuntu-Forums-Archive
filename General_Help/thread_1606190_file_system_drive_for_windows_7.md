---
title: "file system drive for windows 7"
date: 2010-10-26
forum: General Help
---

### Post by timeoutmode on 2010-10-26
hi..

guys is it good that i can see the drive where my windows 7 is installed? and if i want to shrink or expand my ubuntu drive.. where will i do it? in windows 7 or in ubuntu? sorry my first day using ubuntu..

---

### Post by Mark Phelps on 2010-10-26
> **timeoutmode said:**
> hi..

guys is it good that i can see the drive where my windows 7 is installed? 
"See" -- yes; Change -- NO.  Win7 is very finicky about its OS partition.  As long as you're only mounting the partition read-only, there are no problems.  But if you use Places and mount it read/write, you're risking corrupting the filesystem and rendering it unbootable.

So, before messing with the partition, you should boot into Win7, open the Backup feature, create and burn a Win7 Repair CD.  You will need that later to repair the Win7 boot loader should it become corrupted.
>  ... and if i want to shrink or expand my ubuntu drive.. where will i do it? ...
If, in fact, you have installed Ubuntu in its own separate partition, you should use GParted to change the partition size.  Since you can't do that inside Ubuntu (because the partition is mounted), you should go to distrowatch.com, download a burn a GParted LiveCD, boot from that, and use it to do the partition work for Linux partitions.

---

### Post by timeoutmode on 2010-11-02
wow my super late reply,, thank you so much.. i have everything set.. i have repair disc for win7 and complete disk image.. if anyone ever read this thread,, i made my windows 7 file system accessible through ubuntu.. and also installed avast if ever i wanted to send files in it. i have also successfully extended my partition using gparted live cd.

---

