---
title: "unable to boot into ubuntu 11.10 - Kernel Panic"
date: 2012-01-20
forum: General Help
---

### Post by jackal_79 on 2012-01-20
Dear All, I had recently updated some packages on my system that created some dependency errors and latter error on when i tried to boot it was going into grub rescue.I booted with live cd and reinstalled grub.now iam getting boot loader and able to boot into windows xp but not into ubuntu.i tried both current and previous kernel version.system shows a black screen and gets stuck. i have run a boot info script and pasting the results.please help urgently.

---

### Post by carl4926 on 2012-01-20
Use the Ubuntu CD and chroot in to your system
You should be able check your packaging with synaptic and fix as required

---

### Post by drs305 on 2012-01-20
At what point do you get the black screen? Do you see the Grub menu, then it starts to boot and ends up at a blinking cursor? That's my guess since you said you tried 2 kernels.

If this is the case, press 'e' to edit the first menuentry, cursor to the end of the 'linux' line, then remove 'quiet splash' and add 'nomodeset'. Press CTRL-x to boot.

If it now boots to the Desktop, try installing your video card's drivers via 'Additional Drivers' (DASH Home - upper left icon, then start typing Additinal Drivers until it appears below).

---

### Post by jackal_79 on 2012-01-20
> **drs305 said:**
> At what point do you get the black screen? Do you see the Grub menu, then it starts to boot and ends up at a blinking cursor? That's my guess since you said you tried 2 kernels.

If this is the case, press 'e' to edit the first menuentry, cursor to the end of the 'linux' line, then remove 'quiet splash' and add 'nomodeset'. Press CTRL-x to boot.

If it now boots to the Desktop, try installing your video card's drivers via 'Additional Drivers' (DASH Home - upper left icon, then start typing Additinal Drivers until it appears below).

Tried it not working.Actually iam getting a whole bunch of errors related to media or hard disk and gets stuck in the end.Can you check on the attachment i have added and advice?

---

### Post by carl4926 on 2012-01-20
Boot the Ubuntu CD
Start Gparted and check the partitions for errors

---

### Post by drs305 on 2012-01-20
What *carl4926* said. Perform a fsck check.  If Gparted isn't working for you, run the following from the command line:
```
sudo umount /dev/sda10  # Ensures the partition isn't mounted.
sudo e2fsck -f -y -v /dev/sda10 # Checks disk and attempts to fix errors.
```

---

### Post by jackal_79 on 2012-01-20
> **drs305 said:**
> What *carl4926* said. Perform a fsck check.  If Gparted isn't working for you, run the following from the command line:
```
sudo umount /dev/sda10  # Ensures the partition isn't mounted.
sudo e2fsck -f -y -v /dev/sda10 # Checks disk and attempts to fix errors.
```

I tried that.posting the results of fdisk(Please check on the warning on 1st line) and e2fsck command.
=================================================
ubuntu@ubuntu:/$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11b411b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   c  W95 FAT32 (LBA)
/dev/sda2        30717950   488375999   228829025    f  W95 Ext'd (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f3c9188

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976773167   488386552+  42  SFS

Disk /dev/sdc: 1998 MB, 1998519808 bytes
32 heads, 63 sectors/track, 1936 cylinders, total 3903359 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31772be2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     3902975     1951456+   6  FAT16
ubuntu@ubuntu:/$ 
===========================================================================
e2fsck command error:
===========================================================================
ubuntu@ubuntu:/$ sudo e2fsck  -f -y -v /dev/sda10
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: No such file or directory while trying to open /dev/sda10
Possibly non-existent device?
ubuntu@ubuntu:/$ 
==================================================================

---

### Post by jackal_79 on 2012-01-20
Now again system is booting in grub rescue mode.

---

### Post by carl4926 on 2012-01-21
But that fdisk info doesn't make sense compared to your attachment in post #1

You had

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   c W95 FAT32 (LBA)
/dev/sda2          30,717,950   488,375,999   457,658,050   f W95 Extended (LBA)
/dev/sda5          71,682,093   153,597,464    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda6         153,597,528   255,995,774   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda7         255,995,838   419,842,709   163,846,872   7 NTFS / exFAT / HPFS
/dev/sda8         419,842,773   488,375,999    68,533,227   7 NTFS / exFAT / HPFS
/dev/sda9          69,786,423    71,682,029     1,895,607  82 Linux swap / Solaris
/dev/sda10         30,717,952    65,595,391    34,877,440  83 Linux
/dev/sda11         65,597,440    69,785,599     4,188,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,773,167   976,773,105  42 SFS

```

Did you delete your partitions?
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11b411b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   c  W95 FAT32 (LBA)
/dev/sda2        30717950   488375999   228829025    f  W95 Ext'd (LBA)

```

---

### Post by jackal_79 on 2012-01-21
> **carl4926 said:**
> But that fdisk info doesn't make sense compared to your attachment in post #1

You had

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    30,716,279    30,716,217   c W95 FAT32 (LBA)
/dev/sda2          30,717,950   488,375,999   457,658,050   f W95 Extended (LBA)
/dev/sda5          71,682,093   153,597,464    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda6         153,597,528   255,995,774   102,398,247   7 NTFS / exFAT / HPFS
/dev/sda7         255,995,838   419,842,709   163,846,872   7 NTFS / exFAT / HPFS
/dev/sda8         419,842,773   488,375,999    68,533,227   7 NTFS / exFAT / HPFS
/dev/sda9          69,786,423    71,682,029     1,895,607  82 Linux swap / Solaris
/dev/sda10         30,717,952    65,595,391    34,877,440  83 Linux
/dev/sda11         65,597,440    69,785,599     4,188,160  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,773,167   976,773,105  42 SFS

```

Did you delete your partitions?
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11b411b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30716279    15358108+   c  W95 FAT32 (LBA)
/dev/sda2        30717950   488375999   228829025    f  W95 Ext'd (LBA)

```

No, ihave not deleted any partitions.Now iam only getting grub rescue.But if i use ubuntu CD i can manually mount rest of the windows partitions.

---

### Post by carl4926 on 2012-01-21
Have you tried to chroot in to your installed system?

---

### Post by jackal_79 on 2012-01-21
> **carl4926 said:**
> Have you tried to chroot in to your installed system?

No.How do i do that?

---

### Post by carl4926 on 2012-01-21
Boot the live CD

```
sudo mount /dev/sda10 /mnt
```
```
sudo mount --bind /dev /mnt/dev
```
```
sudo chroot /mnt
```

You can now use apt-get to update/upgrade or more

---

### Post by jackal_79 on 2012-01-21
> **carl4926 said:**
> Boot the live CD

```
sudo mount /dev/sda10 /mnt
```
```
sudo mount --bind /dev /mnt/dev
```
```
sudo chroot /mnt
```

You can now use apt-get to update/upgrade or more

Will that also bring back my grub? As i said earlier now iam booting directly to grub rescue>

---

### Post by carl4926 on 2012-01-21
If you did the above chroot

Now do
```
update-grub

```
then
```
grub-install /dev/sda
```
And you're done

---

### Post by jackal_79 on 2012-01-21
> **carl4926 said:**
> If you did the above chroot

Now do
```
update-grub

```
then
```
grub-install /dev/sda
```
And you're done

Well, chroot part worked.Then i ran update-grub.I got this error:
====================================================================
ubuntu@ubuntu:~$ sudo update-grub
error: cannot seek `/dev/sdb'.
error: cannot seek `/dev/sdb'.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ 
========================================================================

what now?

---

### Post by carl4926 on 2012-01-21
You may need to mount it
I think this will do OK
```
sudo mount /dev/sdb1 /media
```

Might be easier though if you could boot your system with SuperGrubDisk

---

### Post by jackal_79 on 2012-01-21
> **carl4926 said:**
> You may need to mount it
I think this will do OK
```
sudo mount /dev/sdb1 /media
```

Might be easier though if you could boot your system with SuperGrubDisk

Thing is i have sdb1 and sdb2. only 1 is listed in this fdisk.Please check my results.txt attachment.should i mount both?how do i do that?

---

### Post by carl4926 on 2012-01-21
Like I said
> Might be easier though if you could boot your system with SuperGrubDisk

Have you tried?

---

### Post by jackal_79 on 2012-01-22
> **carl4926 said:**
> Like I said


Have you tried?

I have no idea what that is.How do i get one?

---

### Post by carl4926 on 2012-01-22
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

You burn it to a cd
Boot from it
You should get an option to boot your installed Ubuntu

---

### Post by jackal_79 on 2012-01-22
> **carl4926 said:**
> [http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)

You burn it to a cd
Boot from it
You should get an option to boot your installed Ubuntu


I only have 1 dvdrw drive which iam currently using for booting in live cd.so for writing i will have to find another way.It will take me sometime to do that.I'll try and get back to you.Meanwhile i have managed to capture some of the errors while booting onto my ubuntu.these are some of last messages before system hangs.Please see if you can make something out of it.

[http://www.4shared.com/folder/zdGW2IHR/_online.html](http://www.4shared.com/folder/zdGW2IHR/_online.html)
or
[[img]http://s19.postimage.org/5b7jyyg4v/IMG_7410.jpg[/img]](http://postimage.org/image/5b7jyyg4v/)

[[img]http://s19.postimage.org/rbshtbo6n/IMG_7409.jpg[/img]](http://postimage.org/image/rbshtbo6n/)

---

### Post by jackal_79 on 2012-01-22
Does anyone have any idea?

---

### Post by carl4926 on 2012-01-22
Have you run a fsck
GParted from a Ubuntu live cd can do this

---

### Post by jackal_79 on 2012-01-23
> **carl4926 said:**
> Have you run a fsck
GParted from a Ubuntu live cd can do this

Do i have to unmount drives before running FSCK ? Please share the command

---

### Post by drs305 on 2012-01-23
> **jackal_79 said:**
> Do i have to unmount drives before running FSCK ? Please share the command

Yes you do. You can unmount the 'device' or the mountpoint. 

Examples for /dev/sda5 on /media/12345678:
```
sudo umount /dev/sda5
*or*
sudo umount /media/12345678
*then to check - the partition should not be in the results:*
mount
```

---

### Post by jackal_79 on 2012-01-28
> **drs305 said:**
> Yes you do. You can unmount the 'device' or the mountpoint. 

Examples for /dev/sda5 on /media/12345678:
```
sudo umount /dev/sda5
*or*
sudo umount /media/12345678
*then to check - the partition should not be in the results:*
mount
```

I have tried fsck and gparted.This is what i got for fsck.
================================================

ubuntu@ubuntu:~$ sudo fsck /dev/sda10
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda10: clean, 210581/1091296 files, 1355677/4359680 blocks
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck from util-linux 2.19.1
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1
ubuntu@ubuntu:~$ 
===================================================================
Iam unable to run fsck or gparted on windows partitions.iam getting no devices fount.

kindly suggest.Also my sdb2 is still not listing on fdisk command

---

### Post by drs305 on 2012-01-28
jackal_79,

fsck checks/repairs linux partitions. Although there is a check of NTFS (Windows partitions available), it is better to run the checks via Windows own disk checking command - chkdsk.

The usual Windows command is "chkdsk [drive:] /f" but I'm not a Windows user so someone more familiar with it will have to give you more specific information if you can't find the answer via searching.

---

### Post by jackal_79 on 2012-01-28
> **drs305 said:**
> jackal_79,

fsck checks/repairs linux partitions. Although there is a check of NTFS (Windows partitions available), it is better to run the checks via Windows own disk checking command - chkdsk.

The usual Windows command is "chkdsk [drive:] /f" but I'm not a Windows user so someone more familiar with it will have to give you more specific information if you can't find the answer via searching.

Ok.Leave the windows part.now fsck on linux partition is showing clean.But it is still not booting and showing the errors (img) attached on my earlier posts.Any idea on how to rectify that?

---

### Post by drs305 on 2012-01-28
From the screenshots I see a few mentions of read errors but I'm not good at analyzing a lot of those messages.

It's been a week since your first post. Have you considered reformatting the partition and reinstalling the OS. I don't often recommend this, but it may be quicker than trying to fix a broken system. 

There are a couple of caveats, you would need to back up any data files on the Ubuntu partition (such as those you've stored in your $HOME folder). You would also lose extra installed apps and customizations. But it's something to consider.

If you want to continue trying to repair the installation, a new copy of the RESULTS.txt might be helpful so we have the latest information.

---

### Post by jackal_79 on 2012-01-28
> **drs305 said:**
> From the screenshots I see a few mentions of read errors but I'm not good at analyzing a lot of those messages.

It's been a week since your first post. Have you considered reformatting the partition and reinstalling the OS. I don't often recommend this, but it may be quicker than trying to fix a broken system. 

There are a couple of caveats, you would need to back up any data files on the Ubuntu partition (such as those you've stored in your $HOME folder). You would also lose extra installed apps and customizations. But it's something to consider.

If you want to continue trying to repair the installation, a new copy of the RESULTS.txt might be helpful so we have the latest information.

Please find a new copy of results.txt

---

### Post by jackal_79 on 2012-01-29
I have re-installed my ubuntu 11.10 and now my system is booting onto ubuntu 11.10.Only problem is, it is not showing any bootloader and loading ubuntu directly.My windows partitions are there but iam unable to load windows.What to do?

---

### Post by drs305 on 2012-01-29
> **jackal_79 said:**
> I have re-installed my ubuntu 11.10 and now my system is booting onto ubuntu 11.10.Only problem is, it is not showing any bootloader and loading ubuntu directly.My windows partitions are there but iam unable to load windows.What to do?

Have you run "sudo update-grub" since reinstalling? Sometimes Grub 2 doesn't pick up Windows the first time and this will force it to search again.

The default behavior of Grub 2 is to not display the menu unless it knows of the existance of another OS. If update-grub finds Windows, it should add it to the menu and the menu will display on boot.

Watch the terminal while update-grub runs. You should see it report finding Windows.

---

### Post by jackal_79 on 2012-01-30
> **drs305 said:**
> Have you run "sudo update-grub" since reinstalling? Sometimes Grub 2 doesn't pick up Windows the first time and this will force it to search again.

The default behavior of Grub 2 is to not display the menu unless it knows of the existance of another OS. If update-grub finds Windows, it should add it to the menu and the menu will display on boot.

Watch the terminal while update-grub runs. You should see it report finding Windows.

I Got this:
===========================================================
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
=====================================================
This i think is the problem why my windows is also not booting.How do i correct my sdb?

---

### Post by drs305 on 2012-01-30
I"ve not seen that error although a search does find reports of it.

Have you tried opening Gparted to see if it can read sdb? 

I don't really know how to correct the error, especially as it concerns a Windows drive. Other than performing a chkdsk on sdb from a Windows repair disk I really don't know how to eliminate the error. I'll take a look around and let you know if I find anything.


**[COLOR="DarkRed"]Added: [/COLOR]**The RESULTS.txt shows partition errors on sdb and I suspect that is the issue. Have you resized or done any other partition operations on your Windows partitions using Gparted rather than a Windows partitioning tool? It also shows the sdb1 filesystem as SFS, with which I'm not familiar.

---

### Post by jackal_79 on 2012-01-30
> **drs305 said:**
> I"ve not seen that error although a search does find reports of it.

Have you tried opening Gparted to see if it can read sdb? 

I don't really know how to correct the error, especially as it concerns a Windows drive. Other than performing a chkdsk on sdb from a Windows repair disk I really don't know how to eliminate the error. I'll take a look around and let you know if I find anything.


**[COLOR="DarkRed"]Added: [/COLOR]**The RESULTS.txt shows partition errors on sdb and I suspect that is the issue. Have you resized or done any other partition operations on your Windows partitions using Gparted rather than a Windows partitioning tool? It also shows the sdb1 filesystem as SFS, with which I'm not familiar.


i think gparted is not even showing sda.it keeps on searching for a long time.eventually i had to close it.

---

### Post by drs305 on 2012-01-30
> **jackal_79 said:**
> i think gparted is not even showing sda.it keeps on searching for a long time.eventually i had to close it.

sda and sdb may be reversed from what you see in RESULTS.txt.

In gparted, if a drive is giving you problems so it won't open you can always omit it by specifying a specific drive: "gksu gparted /dev/sdb"

You could also try Testdisk to snoop around the problem drive.

---

### Post by jackal_79 on 2012-01-30
> **drs305 said:**
> sda and sdb may be reversed from what you see in RESULTS.txt.

In gparted, if a drive is giving you problems so it won't open you can always omit it by specifying a specific drive: "gksu gparted /dev/sdb"

You could also try Testdisk to snoop around the problem drive.

Ok. I got it.I got sdb1.But my sdb2 is still missing.How to find it?

---

### Post by drs305 on 2012-01-30
> **jackal_79 said:**
> Ok. I got it.I got sdb1.But my sdb2 is still missing.How to find it?

If sdb is your 500GB drive, your RESULTS.txt shows only one partition encompassing the entire drive. How large is sdb1 now? If it shows the entire drive but you had two or more partitions, you might be able to restore them using TestDisk.

Here is a howto on TestDisk, although not having identified the problem completely I really don't know if it is one Testdisk can solve.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by jackal_79 on 2012-01-31
> **drs305 said:**
> If sdb is your 500GB drive, your RESULTS.txt shows only one partition encompassing the entire drive. How large is sdb1 now? If it shows the entire drive but you had two or more partitions, you might be able to restore them using TestDisk.

Here is a howto on TestDisk, although not having identified the problem completely I really don't know if it is one Testdisk can solve.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

Yes, sdb is a 500 GB drive with 2 partitions.Now after loading in gparted sdb1 is showing 436Gb.Please suggest.

Also, for my earlier problem iam still not getting grub.System is directly booting on ubuntu.Is it related to my above problem?

One more thing, iam able to see and load my missing sdb2 when iam in ubuntu

---

### Post by drs305 on 2012-01-31
> **jackal_79 said:**
> 
Also, for my earlier problem iam still not getting grub.System is directly booting on ubuntu.Is it related to my above problem?

First - what follows assumes it's your normal Ubuntu that is booting (sda10) and not a Live CD.

Normally when Windows isn't found we just run "sudo update-grub" and it appears in the menu. In your case, Windows is already in the menu and the settings show that Grub 2 is instructed to display the menu for 10 seconds. So I'm not sure why the menu isn't displaying.

Let's try the blunt force method to get it to display. This is a temporary fix just to isolate the problem. The command directly edits grub.cfg and would be overwritten the next time 'update-grub' is run. So just run this command, which sets the timeout at -1. This setting should keep the menu displayed until you make a choice. We'll see if it now displays the Windows menu and figure out what to do next to make it permanent.

```
sudo sed -i 's/set timeout=10/set timeout=-1/g' /boot/grub/grub.cfg
```

> 
Yes, sdb is a 500 GB drive with 2 partitions.Now after loading in gparted sdb1 is showing 436Gb.Please suggest.

One more thing, iam able to see and load my missing sdb2 when iam in ubuntu

The sdb partition situation still puzzles me. The one partition RESULTS.txt finds is SFS, a format that is either wrong or one I'm not familiar with. I've read a bit about it since seeing it in your RESULTS.txt. 

It's possible you need to reset the partition type using TestDisk or some other app, and also perhaps reset the geometry, but I would not do either until you get some better and more complete advice.

Depending on how large your sdb2 is when you are able to see it, you might try either copying the contents or copying the partition elsewhere to preserve the contents should something make it inaccessible later.

---

### Post by jackal_79 on 2012-02-01
> **drs305 said:**
> First - what follows assumes it's your normal Ubuntu that is booting (sda10) and not a Live CD.

Normally when Windows isn't found we just run "sudo update-grub" and it appears in the menu. In your case, Windows is already in the menu and the settings show that Grub 2 is instructed to display the menu for 10 seconds. So I'm not sure why the menu isn't displaying.

Let's try the blunt force method to get it to display. This is a temporary fix just to isolate the problem. The command directly edits grub.cfg and would be overwritten the next time 'update-grub' is run. So just run this command, which sets the timeout at -1. This setting should keep the menu displayed until you make a choice. We'll see if it now displays the Windows menu and figure out what to do next to make it permanent.

```
sudo sed -i 's/set timeout=10/set timeout=-1/g' /boot/grub/grub.cfg
```



The sdb partition situation still puzzles me. The one partition RESULTS.txt finds is SFS, a format that is either wrong or one I'm not familiar with. I've read a bit about it since seeing it in your RESULTS.txt. 

It's possible you need to reset the partition type using TestDisk or some other app, and also perhaps reset the geometry, but I would not do either until you get some better and more complete advice.

Depending on how large your sdb2 is when you are able to see it, you might try either copying the contents or copying the partition elsewhere to preserve the contents should something make it inaccessible later.

I tried the command"
sudo sed -i 's/set timeout=10/set timeout=-1/g' /boot/grub/grub.cfg".Now iam getting bootloader menu.But Windows is not listed on it.How do i make windows appear in this menu and boot to windows?

---

### Post by drs305 on 2012-02-01
I am about to head out on a business trip and found your message as I checked my computer for the last time.

You can try copying the Windows menuentry to /etc/grub.d/40_custom to see if that allows it to be seen in the menu (don't forget to update-grub). Don't forget to run 'sudo update-grub' after saving the file. If you need more help on how to do this just ask and someone may come along to help.

Since this thread is getting a bit old, with lots of posts, you might have better success starting a new thread with a title about Grub and missing Windows. Include a copy of the RESULTS.txt

---

