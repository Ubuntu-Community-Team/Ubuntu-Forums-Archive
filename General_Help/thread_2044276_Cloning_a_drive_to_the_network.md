---
title: "Cloning a drive to the network"
date: 2012-08-19
forum: General Help
---

### Post by Zukaro on 2012-08-19
How can I make an clone of my entire hard drive to a network drive?  I know of dd but I don't think that can clone to the network, also, I don't want to lose any files on my network drive.

But I don't want to just backup my files, as I already have those backed up, I want to backup the entire OS and all partitions (just in case something happens to it I want to be able to just load up the clone and have it exactly as it used to be with all the settings I have and such).

I can't seem to find anything on Google about this (it's all talking about an external hard drive or something else connected through USB).

---

### Post by Rexilion on 2012-08-19
What you need either one of the below:

- partition information
fdisk -l output:


root@Delta:~# LC_ALL=C fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     9764863     4881408   82  Linux swap / Solaris
/dev/sda2   *     9764864    58593279    24414208   83  Linux
/dev/sda3        58593280   156301311    48854016   83  Linux

Above information will allow you to reconstruct the disk layout.

- MBR backup:
dd if=/dev/sda of=mbr_backup bs=512 count=1

The MBR backup is more 1:1, but comes with the disadvantage that it cannot be easily adapted/modified.

---

