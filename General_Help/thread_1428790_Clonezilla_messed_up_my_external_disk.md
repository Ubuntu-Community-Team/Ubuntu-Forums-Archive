---
title: "Clonezilla messed up my external disk"
date: 2010-03-13
forum: General Help
---

### Post by ujjain on 2010-03-13
[FONT=Arial][SIZE=2]Tuesday night I wanted to make a backup of my Ubuntu ext4 partition via Clonezilla so I configured that an image had to be made and it would be saved on the NTFS external disk. But it said it needed 23 hours to create a 5gb backup, so I resetted my computer as this took too long. But after this, Ubuntu nor Windows recognized my drive.

I called Seagate and they told me after troubleshooting 30 minutes, that there is no option of fixing the drive and I had to send it to RMA. What could be wrong? Clonezilla works via a bootable ISO on Debian. The disk drive is still spinning. I already rebooted the external drive, but it's not working. In Linux the disk is no longer mounted and cannot be mounted:```
brw-rw---- 1 root disk 8, 16 2010-03-12 00:50 /dev/sdb
brw-rw---- 1 root disk 8, 32 2010-03-12 00:50 /dev/sdc[FONT=monospace]
[/FONT]brw-rw---- 1 root disk 8, 48 2010-03-12 00:50 /dev/sdd[FONT=monospace]
[/FONT]brw-rw---- 1 root disk 8, 64 2010-03-12 00:50 /dev/sde
```What could have happened[/SIZE][/FONT][FONT=Arial][SIZE=2]?[/SIZE][/FONT][FONT=Arial][SIZE=2] Would the data still be accessible on the internal drive? Did I just loose 1.5TB data that was stored on the external disk?
[/SIZE][/FONT]

---

### Post by ujjain on 2010-03-21
I really need advice on recovering my data. What is the chance that all my data is lost because of Clonezilla?

---

### Post by howefield on 2010-03-22
> **ujjain said:**
> What is the chance that all my data is lost because of Clonezilla?

If you have spent 30 minutes with your hard disk vendor trying to recover the disk and failed, I'd guess that you may need a data recovery specialist to get anything from the disk. However, this may be very expensive, but worth investigating.

To directly answer the question, there is zero chance that you have lost data because of Clonzilla, the real culprit here is user error and lack of a suitable backup strategy.

---

### Post by ujjain on 2010-03-22
I had to break open the disk enclosure and there was no damage on the internal disk and I successfully transferred all data from the 2TB internal disk to my own primary disk. I am still puzzled on how Clonezilla broke my external disk, as the internal disk was still fine... also, I am not sure who's to blame here, Clonezilla, Seagate or myself.

Although my back-up procedures must definitely be re-thought, I do not think I am to blame that the external drive no longer worked.

---

### Post by blueridgedog on 2010-03-22
Your drive appears to have a hardware failure.  It is not likely that the failure is attributable to the last program you ran, but rather a manufacturing defect.  It may simply be the reset while the head was writing.  

Does the disk show up at all in the output of 

```
sudo fdisk -l
```

??

If so, then testdisk may help you.  It is a great program.

---

