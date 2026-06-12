---
title: "Bootable 16GB thumb drive"
date: 2010-02-13
forum: General Help
---

### Post by dmillerw on 2010-02-13
I'm going to be making a custom minimal Ubuntu install for my thumb drive, and I've got a question.

I've got a 16GB thumb drive, is it possible to make a 4GB partition on it to hold Ubuntu, and still use the rest for normal file storage?

---

### Post by ironclaw on 2010-02-13
Yes, that's what I do with my 8 GB USB flash drive. Here is my "fdisk -l" output if you are interested:
```
Disk /dev/sdc: 8086 MB, 8086618112 bytes
249 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15438 * 512 = 7904256 bytes
Disk identifier: 0x000bcdf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         751     5796938    c  W95 FAT32 (LBA)
/dev/sdc2   *         752        1023     2099568   1c  Hidden W95 FAT32 (LBA)
```

'/dev/sdc2' holds a live USB of BackTrack4 created from UNetbootin, and I can boot from it perfectly. When the USB drive is plugged into a Windows or Ubuntu machine, only '/dev/sdc1' automounts, which is the intended behavior.

---

### Post by pizza-is-good on 2010-02-13
Yep, although windows will only see your ubuntu partition, and not your data one.

It is a very good idea. I did that while back, until I put ubuntu back on my 1 GB drive and kept my other one fully for data

---

### Post by Yogotiss on 2010-02-13
> **dmillerw said:**
> I'm going to be making a custom minimal Ubuntu install for my thumb drive, and I've got a question.

I've got a 16GB thumb drive, is it possible to make a 4GB partition on it to hold Ubuntu, and still use the rest for normal file storage?

Yes it is possible but just keep in mind that after accomplishing that task with a 16GB flash media. Most Linux Operating System will display 2 folders with both partitions when plugging it in.

---

### Post by ironclaw on 2010-02-13
> **pizza-is-good said:**
> Yep, although windows will only see your ubuntu partition, and not your data one.

It is a very good idea. I did that while back, until I put ubuntu back on my 1 GB drive and kept my other one fully for data
I think that if you put the data partition as the first partition in the drive, Windows will mount that instead of the Ubuntu partition. It works in my configuration. Make sure that you turn on the 'boot' flag for the Ubuntu partition so that the BIOS will know to boot from that instead of the first partition.

> **Yogotiss said:**
> Yes it is possible but just keep in mind that after accomplishing that task with a 16GB flash media. Most Linux Operating System will display 2 folders with both partitions when plugging it in.
If you change the partition type to a hidden FAT (e.g., 1c in fdisk), Ubuntu 9.10 won't automount the partition. It used to be that Ubuntu would mount it, but something changed in 9.10 that made it check whether the partition was hidden or not.

---

### Post by dmillerw on 2010-02-13
Alright awesome, thanks.

---

### Post by C.S.Cameron on 2010-02-14
If you do a Full install to your thumbdrive you can select manual partitioning then leave however much FAT32 partition as you want for sharing with Windows then make a "/" ext4 partition for Ubuntu and then a "/home partition if you wish. Some people would also suggest adding some swap space.

---

