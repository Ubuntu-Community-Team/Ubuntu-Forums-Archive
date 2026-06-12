---
title: "GParted Resize Hangs"
date: 2011-06-01
forum: General Help
---

### Post by Marionumber1 on 2011-06-01
I have a triple boot of Win 7, Ubuntu, and FreeDOS. I have a partition layout as follows:

1: EFI System Partition
2: Windows NTFS
3: FreeDOS FAT
4: Extended
5: Ubuntu EXT4
6: FAT32 Data
7: Ubuntu Swap

I decided to move the extended partition left. Worked. Now I moved the logical partitions left. Ubuntu goes fine, but now something weird happens. It says it moved on to my data partition (/dev/sda6), but it lists the size the same as Ubuntu, and the progress bar just moves back and forth. In details for my data partition, Moving Filesystem just says Using Libparted. In Disk Utility, my data partition is gone! Should I wait it out or abort.

---

### Post by Marionumber1 on 2011-06-01
Oh wow. Just as I posted this, it got solved. Please lock this.

---

### Post by srs5694 on 2011-06-02
***Never*** interrupt a partition resize or move operation unless you have no other choice (say, if the computer has clearly hung completely).

One issue I noticed: Your partition setup is very peculiar. Few Master Boot Record (MBR) disks have an EFI System Partition (ESP). There is an MBR type code for an ESP (0xEF), but that's a very peculiar feature. ESPs are generally restricted to GUID Partition Table (GPT) disks, which don't have extended partitions.

Some people mistakenly believe that partitions of type 0xEE are ESPs, but they aren't; those are GPT *protective* partitions. If that's what you've got, and if you've got an extended partition, you're playing with fire, since that indicates a GPT disk with a hybrid MBR and extended partitions -- an *extremely* dangerous combination!

If you're certain that's an ESP on your disk, and especially if you understand why it's there, then it's not a problem. (You might end up with that configuration if it was a GPT disk that you converted to MBR form using gdisk or some other tool.) I just want to be sure you understand what's on your own disk so that you don't shoot yourself in the foot with a hazardous disk layout.

---

### Post by Marionumber1 on 2011-06-17
It's there because I was planning to install Mac OS X with a modified install program that allows MBR install.

Thanks for the response.

---

