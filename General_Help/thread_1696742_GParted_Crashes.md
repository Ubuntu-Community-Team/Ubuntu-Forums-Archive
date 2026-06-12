---
title: "GParted Crashes"
date: 2011-02-27
forum: General Help
---

### Post by Zythyr on 2011-02-27
I downloaded Ubuntu Netbook 10.10 and created a live USB to install it on my MSI Wind U123 netbook. 

I am unable to install Ubuntu or JoliCloud because installation hangs/freeze every time I try to install it. Please see this topic for more info: [http://ubuntuforums.org/showthread.php?t=1694861](http://ubuntuforums.org/showthread.php?t=1694861). 

To troubleshoot the issue, I decided to run the live version of Ubuntu and format one of the partitions to ext3 prior to trying to install Ubuntu/JoliCloud. But everytime I try to run GParted, the program crashes. 

I tried multiple times. Could this be a hardware issue on my netbook?

---

### Post by dr_latino999 on 2011-02-27
> **Zythyr said:**
> I downloaded Ubuntu Netbook 10.10 and created a live USB to install it on my MSI Wind U123 netbook. 

I am unable to install Ubuntu or JoliCloud because installation hangs/freeze every time I try to install it. Please see this topic for more info: [http://ubuntuforums.org/showthread.php?t=1694861](http://ubuntuforums.org/showthread.php?t=1694861). 

To troubleshoot the issue, I decided to run the live version of Ubuntu and format one of the partitions to ext3 prior to trying to install Ubuntu/JoliCloud. But everytime I try to run GParted, the program crashes. 

I tried multiple times. Could this be a hardware issue on my netbook?

Nope, issue on gparted on the livecd.

```

sudo apt-get update
sudo apt-get install gparted

```

No more problem.

---

### Post by Zythyr on 2011-02-27
> **dr_latino999 said:**
> Nope, issue on gparted on the livecd.

```

sudo apt-get update
sudo apt-get install gparted

```No more problem.

I put in the live USB, then booted into Ubuntu Netbook 10.10. 

I connected to the internet. 

Then I went to terminal and typed in *sudo apt-get update* and then it got a list of updates. 
Then I typed in *sudo apt-get isntall gparted* and then it did its thing... 

I then typed *exit* to close the terminal. 

I started Gparted and it crashed again. :( 

The issue it still not solved.

---

### Post by dr_latino999 on 2011-02-27
> **Zythyr said:**
> I put in the live USB, then booted into Ubuntu Netbook 10.10. 

I connected to the internet. 

Then I went to terminal and typed in *sudo apt-get update* and then it got a list of updates. 
Then I typed in *sudo apt-get isntall gparted* and then it did its thing... 

I then typed *exit* to close the terminal. 

I started Gparted and it crashed again. :( 

The issue it still not solved.

That's strange. I was having the crash problems on a test bed for the last two weeks of migration, and I would have to perform those two steps each go. You may be experiencing another problem. 

Have you tried any other live versions such as 10.04?

---

### Post by dcstar on 2011-02-27
> **Zythyr said:**
> I downloaded Ubuntu Netbook 10.10 and created a live USB to install it on my MSI Wind U123 netbook. 

I am unable to install Ubuntu or JoliCloud because installation hangs/freeze every time I try to install it. Please see this topic for more info: [http://ubuntuforums.org/showthread.php?t=1694861](http://ubuntuforums.org/showthread.php?t=1694861). 

To troubleshoot the issue, I decided to run the live version of Ubuntu and format one of the partitions to ext3 prior to trying to install Ubuntu/JoliCloud. But everytime I try to run GParted, the program crashes. 

I tried multiple times. Could this be a hardware issue on my netbook?

Possibly the existing partitions are corrupted and gparted (or more likely the underlying parted program) cannot understand them.

Manually delete/resize the partitions with another tool, or install **testdisk** to test and repair the partitions.

---

### Post by Zythyr on 2011-02-27
> **dr_latino999 said:**
> That's strange. I was having the crash problems on a test bed for the last two weeks of migration, and I would have to perform those two steps each go. You may be experiencing another problem. 

Have you tried any other live versions such as 10.04?

Maybe I am not using the proper method to update Gparted? I uninstalled Gparted manually and reinstalled it, but it doesn't install the latest version which is 0.8.0

---

### Post by psusi on 2011-02-27
What exactly do you mean by "it crashed"?  Did you get an error dialog?  What did it say?  Does it crash on startup, or do you have to do something first?  Try running gparted from the terminal and see if you get any additional output.

---

### Post by Zythyr on 2011-02-28
> **psusi said:**
> What exactly do you mean by "it crashed"?  Did you get an error dialog?  What did it say?  Does it crash on startup, or do you have to do something first?  Try running gparted from the terminal and see if you get any additional output.

It keeps crashing on start-up. 
The live USB has v0.6.2 of Gparted running. I think there is some issue with that version which make it crash, and also prevents me from installing ubuntu

---

### Post by Zythyr on 2011-02-28
So I tired to start GParted from the terminal and here is the output I got: 
> 
ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 2.3
======================
/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Backtrace has 14 calls on stack:
  14: /lib/libparted.so.0(ped_assert+0x2a) [0x42587a]
  13: /lib/libparted.so.0(ped_geometry_read+0x116) [0x42f5e6]
  12: /lib/libparted.so.0(hfsplus_probe+0x3a1) [0x44f751]
  11: /lib/libparted.so.0(ped_file_system_probe_specific+0x6c) [0x4273dc]
  10: /lib/libparted.so.0(ped_file_system_probe+0x81) [0x4279d1]
  9: /lib/libparted.so.0(+0x4a00c) [0x46600c]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x42e7d5]
  7: /usr/sbin/gpartedbin() [0x80900b6]
  6: /usr/sbin/gpartedbin() [0x809beb5]
  5: /usr/sbin/gpartedbin() [0x80c1dd2]
  4: /usr/lib/libglibmm-2.4.so.1(+0x31e42) [0x16ee42]
  3: /lib/libglib-2.0.so.0(+0x6848f) [0x2de48f]
  2: /lib/libpthread.so.0(+0x5cc9) [0x38ccc9]
  1: /lib/libc.so.6(clone+0x5e) [0x106c6ae]
I previously had Mac installed onto this netbook using a GUID partition scheme. But I removed it and did a clean install of Windows 7, and along with it, I created 3 partitions during windows installation: First partition for WIndows,  second parition was a 10GB for Jolicloud and third parition was also a 10GB for Ubuntu Netbook. 

Below is my fdisk -lu output. 

> 
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5736addd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   271620095   135706624    7  HPFS/NTFS
/dev/sda3       271620096   294146047    11262976    7  HPFS/NTFS
/dev/sda4       294146048   312578047     9216000    7  HPFS/NTFS

Disk /dev/sdb: 4039 MB, 4039114752 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7888896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7887914     3943926    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

Could this be the issue why Gparted is crashing and also Ubuntu/JoliCloud is hanging/freezing during installation? If so, how do I fix this issue?

---

### Post by psusi on 2011-02-28
Yep, you corrupted the partition table by overwriting the MBR with a new msdos partition table, but the GPT is still there.  You need to remove the broken GPT.  Make sure you enter this command EXACTLY as it appears:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1
```

---

### Post by srs5694 on 2011-02-28
Unfortunately, psusi's command will not completely remove the old GPT data; it will remove the primary GPT data that appear at the start of the disk, but not the backup data at the end of the disk. To completely remove the data, I recommend using GPT fdisk (gdisk or sgdisk), as described [here.](http://www.rodsbooks.com/gdisk/wipegpt.html) In brief, download the software from [its Sourceforge page,](http://sourceforge.net/projects/gptfdisk/files/) install it, and then issue the following command:

```

sudo sgdisk --zap /dev/sda

```

There are some caveats and issues, though, so I recommend you read my full page on the issue.

Incidentally, when you post text-mode program output, you should use [noparse]```
[/noparse] and [noparse]
```[/noparse] tags, not [noparse]> [/noparse] and [noparse][/noparse] tags.

---

### Post by Zythyr on 2011-02-28
> **psusi said:**
> Yep, you corrupted the partition table by overwriting the MBR with a new msdos partition table, but the GPT is still there.  You need to remove the broken GPT.  Make sure you enter this command EXACTLY as it appears:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1
```

I ran into this post, [http://georgia.ubuntuforums.org/showpost.php?p=9866163&postcount=8](http://georgia.ubuntuforums.org/showpost.php?p=9866163&postcount=8), and used GDisk to fix the issue!!! 

It works perfect. Thanks for the help everyone.

---

