---
title: "Migrating Ubuntu on to 3TB drive"
date: 2012-04-11
forum: General Help
---

### Post by james25182 on 2012-04-11
Hi,

I am running Ubuntu 10.10. It is installed on a 200GB drive but I ran out of space and purchased a 3TB drive to replace it. I used dd to copy the old drive to the new and the system booted just fine. However, I'm running into the 2TB limit on partitions when trying to either expand the partition or create a new one out of the remaining 2.8TB space. I have found guides on installing onto a >2TB drive but nothing on how to migrate an existing install. Help appreciated!

James

---

### Post by oldfred on 2012-04-11
Old drive is MBR, MBR has a limit of 2TiB or about 2.2TB. Newer drives then should be formated to gpt, which works with new systems with UEFI boot for both Windows & Linux or only Linux in BIOS boot.

I use several smaller drives with gpt and BIOS to boot.

It would be best to do a clean install to new drive and copy /home (is it a separate partition?) and if you have a lot of programs you can reinstall from dpkg export of list of installed apps.

Also there was a bug in grub on very large / (root) partitions. I normally suggest partitioning in advance and / partitions of 25GB with all data in /home or (more advanced) separate data partition(s).

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by james25182 on 2012-04-12
Thanks for the information.

I'm reluctant to do a full reinstall as it would take me forever to get the system back to the state it is now. Is there a way I can backup the O/S, do the partitioning and restore the O/S into the newly partitioned drive?

Thanks again.

James

---

### Post by oldfred on 2012-04-12
I use rsync to backup just data and some settings, but not entire system as I just plan a new install. Not sure if you can go from MBR to gpt with these:

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)


Since you have so much new space. Try creating a new 25GB partition, and another larger partition for /home. Copy with rsync all of your current /home into your new /home partition. And do another install. I think you will find you have all your settings and data. If you like it then you can use dpkg to list all installed packages and reinstall those. Depending on size of /home that may take a will to copy, but a new install can be less than an hour. Just as part of new install be sure to specify the /home partition you created, but DO NOT format it.

To move /home uses rsync - you only need to copy to new partition part of these instructions:
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

In my 640GB drive I have all these installed currently using the same two data partitions (not /home), but my current install 10.10 is in sdb, so only data partitions are shown as mounted.
Karmic, Natty, Lucid, Puppy, Kubuntu, Oneiric and a couple of more 20 to 25GB for other tests. I am not suggesting going beserk like I have, my configuration is now so complex I cannot keep track of what is where. :)

---

### Post by james25182 on 2012-04-16
Many thanks for your help. For future reference this is what I did:

I booted up PartedMagic and ran the following:

```

sudo dd if=/dev/sda of=/dev/sda bs=8192

```
This copied my old disk to my new, MBR and all.

Rebooted to check that this copying had worked then booted back into PartedMagic

I then read the tutorial here: [http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

The simple version of which is to run:
```

gdisk
```
Then hit w to write the GPT partition table to disk. Reboot and then create a big 2.8TB partition in Ubuntu to mount as space for my data. Done!:guitar:




Or...

In reality my system would not boot the GPT disk as I think there is an issue with the BIOS and GPT. At this point I gave up and left my original disk in as a boot disk, used [FONT="Courier New"]gdisk[/FONT] on my new disk to create a new GPT with a 3TB partition and mounted this for data. It's currently balancing on top of my case. I now need to buy a new case with enough space for 2 disks.

James

---

### Post by oldfred on 2012-04-16
To get grub2 to install correctly in a gpt drive with BIOS you have to add a small 1MB bios_grub partition, so grub has a place for core.img.

My new install to my SSD I created both the efi & bios_grub partitions as I hope to get new system this year & expect it to be UEFI, but use bios_grub for now and have efi for the future system.

I used this idea, but with Ubuntu on every drive. Partition is a bit larger with Ubuntu.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

