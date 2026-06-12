---
title: "Vista fails to boot after UBUNTU 10.4 installation."
date: 2010-08-13
forum: General Help
---

### Post by mayotom on 2010-08-13
Recently I installed UBUNTU 10.04 on my Laptop, but since then I have not been able to Boot windows, since then, there is an option at start up for Vista, however when I choose this nothing happens I just get a blank screen and a cursor in the top left corner.

---

### Post by Sef on 2010-08-13
1) Are you dual booting or using WUBI?

2) If you dual booted, how did you partition?

---

### Post by mayotom on 2010-08-13
> **Sef said:**
> 1) Are you dual booting or using WUBI?

2) If you dual booted, how did you partition?

I have used a Dual Boot, I Started using UBUNTU from a memory stick and then partitioned to allow UBUNTU to have 30GB, but the laptop just switched off during the process so I partitioned again and now I have UBUNTU on two partitions of 30GB each and Windows on one of 144GB.

---

### Post by sydbat on 2010-08-13
> **mayotom said:**
> I have used a Dual Boot, I Started using UBUNTU from a memory stick and then partitioned to allow UBUNTU to have 30GB, but the laptop just switched off during the process so I partitioned again and now I have UBUNTU on two partitions of 30GB each and Windows on one of 144GB.How did you partition? Through Windows or the Ubuntu LiveUSB?

Also, I wonder if the powering off might not have completely borked your Windows install.

---

### Post by mayotom on 2010-08-13
I did the Partition from the USB stick, all of the Windows files are still on file, maybe the power off could have caused it, but then again, the partition and installation of UBUNTU at the same time was successful

---

### Post by Mark Phelps on 2010-08-13
Once again -- HOW did you do the partitioning??

Did you use the Win7 Disk Management utility? Or did you use GParted?

IF you did the second, you could very well have corrupted the Win7 boot loader in the process, thus, rendering Win7 unbootable.

Did you go to the trouble to use the Win7 Backup feature to create and burn a Win7 Repair CD -- BEFORE you started messing around with the partitions?

If you did -- then boot from it and run startup repair three times.

---

### Post by mayotom on 2010-08-13
> **Mark Phelps said:**
> Once again -- HOW did you do the partitioning??

Did you use the Win7 Disk Management utility? Or did you use GParted?

IF you did the second, you could very well have corrupted the Win7 boot loader in the process, thus, rendering Win7 unbootable.

Did you go to the trouble to use the Win7 Backup feature to create and burn a Win7 Repair CD -- BEFORE you started messing around with the partitions?

If you did -- then boot from it and run startup repair three times.

Sorry Mark,

I did use gparted for the partition and a back up was created however this disk has vanished while moving recently, so finding it a little difficult to solve.

---

### Post by sydbat on 2010-08-13
> **mayotom said:**
> I did the Partition from the USB stick, all of the Windows files are still on file, maybe the power off could have caused it, but then again, the partition and installation of UBUNTU at the same time was successfulYou might have to redo the Windows MBR. I believe it can be done off the Windows install CD/DVD. If you do not have one, this might help - [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Or this - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Snowbat on 2010-08-13
Some details of mayotom's issue (grub.cfg and output of fdisk -l) over at [http://www.boards.ie/vbulletin/showthread.php?t=2055958823](http://www.boards.ie/vbulletin/showthread.php?t=2055958823)

We discovered that the labels for Windows Recovery Environment and Windows Vista in grub.cfg were swapped.  Trying to boot the actual Vista partition with "drivemap -s (hd0) ${root}" results in a return to the boot menu after a few seconds.  Trying to boot the actual Vista partition without "drivemap -s (hd0) ${root}" results in a blank screen with cursor.

---

