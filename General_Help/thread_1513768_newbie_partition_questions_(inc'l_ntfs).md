---
title: "newbie partition questions (inc'l ntfs)"
date: 2010-06-20
forum: General Help
---

### Post by gedman on 2010-06-20
I'm an Ubuntu newbie, installing 10.04 (UNR) on a dual-boot laptop with Windows 7 x64.

My goal is to have Win7 and UNR dual-boot, with a shared partition for user files.  My plan is to have the following partitions on my 250 GB drive:

[LIST]
[*]Windows7 partition (which I already shrunk to 30 GB)
[*]Windows recovery partition (100 MB)
[*]Ubuntu (20 GB, ext4, Primary, mount point = / )
[*]Swap (4 GB, since I have 2 GB of RAM)
[*]User Files shared partition (196 GB **[COLOR=Red]NTFS[/COLOR]**)
[/LIST]
1) Is NTFS the right format for the user files partition? (I have done lots of Googling on this topic already.)

2) During _installation_ of 10.04 from LiveCD, the installer doesn't have NTFS as an available format when defining new partitions.  But if I load a full UNR session, and then run GParted, I am able to create NTFS partitions.  Why is that?  (Perhaps ntfsprogs is not accessible to the installer?!?)  How should I create the NTFS user files partition?

Thanks!

Gedman

---

### Post by Pollox on 2010-06-20
NTFS should work fine for both Windows and Linux in terms of reading and writing to it.  You could also use a FAT32 partition for it.  Keep in mind you only get 4 primary partitions.  So,
1) Windows 7
2) Windows 7 recovery
3) User files shared
4) Extended partition: put Ubuntu and the Swap partition as logical partitions in here.

If you can't format things as NTFS from the LiveCD (which is odd btw, but perhaps I just never tried it before), then simply leave free space where you want to put that partition, and format it after you install Ubuntu.  Or use Windows 7's partition manager to do it.  You should be able to format anything that is not mounted.  Remember to backup your stuff before you do any partitioning.

---

### Post by gedman on 2010-06-20
Doesn't Ubuntu need to be installed on a Primary partition?  If so, the layout would be

1) Windows 7
2) Windows 7 recovery
3) Ubuntu
4) Extended partition: User files shared and Swap

Also, in the LiveCD installer, do I need to explicitly create the Extended partition, and then explicitly create the Logical partitions within it?  Or, by specifying a partition as "Logical", does the installer simply create the Extended partition without requiring me to specify it explicitly?

Thanks!

Gedman

---

### Post by gedman on 2010-06-20
OK, I found the answer to my question #1.  (Yes, Ubuntu can be installed on a Logical partition).

I'm still needing answer to question #2.  (Do I need to explicitly create an extended partition, or will the install do that for me automatically when I specify my first logical partition?)

Thanks!

---

### Post by Roly25 on 2010-06-20
> **gedman said:**
> OK, I found the answer to my question #1.  (Yes, Ubuntu can be installed on a Logical partition).

I'm still needing answer to question #2.  (Do I need to explicitly create an extended partition, or will the install do that for me automatically when I specify my first logical partition?)

Thanks!

You could quite easily create your Extended partition using the Windows 7 Disk manager snap in for the Admin App. I'm not sure if the Installer will let you create an Extended partition from the Live CD Installer.  You could just Install your Ubuntu 10.04 NBR and swap Partitions as Primary Partitions and keep your files on an external HDD, not as neat a solution as having them on a Partition on your Internal HDD, but they will be kept safe as they are backed up if you need to recover your system or re-install Ubuntu you don't have to remember to backup you files as you just have to un plug the external HDD and they are safe from getting accidentaly deleted.

Roland

---

### Post by gedman on 2010-06-20
I found my answer to #2 (the installer creates the extended partition automatically when specifying a Logical partition).

---

