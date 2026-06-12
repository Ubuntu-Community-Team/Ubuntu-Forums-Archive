---
title: "Grub and missing Windows"
date: 2012-02-02
forum: General Help
---

### Post by jackal_79 on 2012-02-02
Hi, All. This is a continuation of an earlier thread started for a different reason ([http://ubuntuforums.org/showthread.php?t=1912441](http://ubuntuforums.org/showthread.php?t=1912441))
After my earlier problem of not able to boot into ubuntu got resolved(I had to go for the ages old solution of re-installing ubuntu!) i was only able to boot into ubuntu directly without even seeing the bootloader.After the last suggestion from earlier post iam seeing bootloader.But Windows menu is missing.How do i bring it back?

a Copy of my fdisk
================================

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11b411b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   c  W95 FAT32 (LBA)
/dev/sda2        30717950   488375999   228829025    f  W95 Ext'd (LBA)
/dev/sda5        71682093   153597464    40957686    7  HPFS/NTFS/exFAT
/dev/sda6       153597528   255995774    51199123+   7  HPFS/NTFS/exFAT
/dev/sda7       255995838   419842709    81923436    7  HPFS/NTFS/exFAT
/dev/sda8       419842773   488375999    34266613+   7  HPFS/NTFS/exFAT
/dev/sda9        69786423    71682029      947803+  82  Linux swap / Solaris
/dev/sda10       30717952    65595391    17438720   83  Linux
/dev/sda11       65597440    69785599     2094080   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f3c9188

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976773167   488386552+  42  SFS
=================================================================

Only 1 partition of my sdb is listed and the filesystem shown is unknown to me.

---

### Post by jerrrys on 2012-02-03
Have you tried:

sudo update-grub

---

### Post by seawolf167 on 2012-02-03
If, as posted above, the command doesn't work

```
sudo update-grub
```

Then download and run the Boot Info Script from [here]("http://sourceforge.net/projects/bootinfoscript/") then post the results inside [noparse]```

```[/noparse] tags.

---

### Post by jackal_79 on 2012-02-04
> **seawolf167 said:**
> If, as posted above, the command doesn't work

```
sudo update-grub
```

Then download and run the Boot Info Script from [here]("http://sourceforge.net/projects/bootinfoscript/") then post the results inside [noparse]```

```[/noparse] tags.

Yes, When i try that i get this.
==========================================

jackal@jackal-XFX-nForce-650i-Ultra:~$ sudo update-grub
[sudo] password for jackal: 
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Generating grub.cfg ...
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-3.0.0-15-generic
Found initrd image: /boot/initrd.img-3.0.0-15-generic
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
Found memtest86+ image: /boot/memtest86+.bin
done
jackal@jackal-XFX-nForce-650i-Ultra:~$ 
============================================================

---

### Post by jackal_79 on 2012-02-05
> **seawolf167 said:**
> If, as posted above, the command doesn't work

```
sudo update-grub
```

Then download and run the Boot Info Script from [here]("http://sourceforge.net/projects/bootinfoscript/") then post the results inside [noparse]```

```[/noparse] tags.

Please find the results in attachment

---

### Post by Mark Phelps on 2012-02-06
IF the "SFS" is correct for sdb, then it looks like your NTFS partition somehow got converted into a Dynamic Disk -- which Linux distros can't read.

And, while Win7 Disk Management utility does provide the feature to convert Dynamic Disks to Basic Volumes, it is designed to work on EMPTY disks.  So, doing this is likely to erase the contents of SDB.

---

### Post by jackal_79 on 2012-02-11
> **Mark Phelps said:**
> IF the "SFS" is correct for sdb, then it looks like your NTFS partition somehow got converted into a Dynamic Disk -- which Linux distros can't read.

And, while Win7 Disk Management utility does provide the feature to convert Dynamic Disks to Basic Volumes, it is designed to work on EMPTY disks.  So, doing this is likely to erase the contents of SDB.

For all this i need to boot into windows.How do i get my windows back?

---

### Post by oldfred on 2012-02-11
Partition rules are that you can only have 4 primary partitions. But one primary can be converted to the extended partition which can hold many logical partitions. Windows does not convert to extended/logical but dynamic partitions. Best to unconvert if you do not have more than 4 partitions.

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by jackal_79 on 2012-02-11
> **oldfred said:**
> Partition rules are that you can only have 4 primary partitions. But one primary can be converted to the extended partition which can hold many logical partitions. Windows does not convert to extended/logical but dynamic partitions. Best to unconvert if you do not have more than 4 partitions.

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

how does that affect my booting to windows.Infact my windows is still not visible on grub

---

### Post by oldfred on 2012-02-11
There is risk with any partition change, so good backups are important. 

As long as you have dynamic partitions Ubuntu will not work with your Windows.

---

### Post by jackal_79 on 2012-02-12
> **oldfred said:**
> There is risk with any partition change, so good backups are important. 

As long as you have dynamic partitions Ubuntu will not work with your Windows.

What iam trying to say is that i have not made any partition changes in last 2 years.Now, my grub is not visible.And even when it shows there is no windows in it.I want some advice to bring it back.Of course, iam able to see & use all partitions windows and ubuntu.But i need to boot into windows.

---

### Post by oldfred on 2012-02-12
I went back on looked at results.txt. It would have been better to have posted so we could easier review it. Your SFS/dynamic drive is just sdb. Not sure why with one partition it is dynamic.

Your error on sda is something else. Have you tried chkdsk. You have to run chkdsk until it has no errors as it does not fix everything on one pass. You also need to run it on all partitions.

You can use any Windows repairCD to run chkdsk, but not fixes for a different version. I used a Windows 7 repair USB to run chkdsk on my XP install.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by jackal_79 on 2012-02-12
> **oldfred said:**
> I went back on looked at results.txt. It would have been better to have posted so we could easier review it. Your SFS/dynamic drive is just sdb. Not sure why with one partition it is dynamic.

Your error on sda is something else. Have you tried chkdsk. You have to run chkdsk until it has no errors as it does not fix everything on one pass. You also need to run it on all partitions.

You can use any Windows repairCD to run chkdsk, but not fixes for a different version. I used a Windows 7 repair USB to run chkdsk on my XP install.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

thankyou for taking the time!.But if iam not getting the grub will i still be able to use win xp boot cd?.I will try and let you know.

---

### Post by oldfred on 2012-02-12
Grub cannot boot a broken Windows. First you have to repair Windows. You may want to also run the fixMBR, so you know Windows boots on its own, then reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by jackal_79 on 2012-02-18
> **oldfred said:**
> Grub cannot boot a broken Windows. First you have to repair Windows. You may want to also run the fixMBR, so you know Windows boots on its own, then reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Sorry! for the long time.Today i ran the chkdsk drive : /P/R and got the following error:

"The volume appears to contain one or more unrecoverable problems". Now what should i do.It is really important for me to get back my windows.

---

### Post by oldfred on 2012-02-18
I do not think the chkdsk /p /r is correct. You are supposed to use one or the other. Or 
chkdsk c: /p
or 
chkdsk c: /r

And often with chkdsk you have to run it multiple times. Perhaps the incorrect command line was the reason for the reported error?

---

### Post by jackal_79 on 2012-02-19
> **oldfred said:**
> I do not think the chkdsk /p /r is correct. You are supposed to use one or the other. Or 
chkdsk c: /p
or 
chkdsk c: /r

And often with chkdsk you have to run it multiple times. Perhaps the incorrect command line was the reason for the reported error?

i run the command with /p/r twice and got same error both times.Anyway i will try one by one as you suggested and let you know on the result

---

### Post by jackal_79 on 2012-02-26
> **oldfred said:**
> I do not think the chkdsk /p /r is correct. You are supposed to use one or the other. Or 
chkdsk c: /p
or 
chkdsk c: /r

And often with chkdsk you have to run it multiple times. Perhaps the incorrect command line was the reason for the reported error?

i have tried it many times .But got the same error as above.Any ideas?

---

### Post by oldfred on 2012-02-26
Having sda1 as a FAT32 makes it harder to repair. FAT does not include an journal as NTFS or the Linux ext3 or ext4 file systems do.

I find it best to use Windows tools on Windows partitions, but if they do not work there is not much that you can do.

You can try testdisk:
[http://www.cgsecurity.org/wiki/Advanced_FAT_Repair](http://www.cgsecurity.org/wiki/Advanced_FAT_Repair)

If you have files that you have not backed up there are ways to scan hard drive and look for data that may be a file. None are simple or easy to restore data as too much may be lost already.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
See post #22 for results from several recovery tools.
[http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)

---

