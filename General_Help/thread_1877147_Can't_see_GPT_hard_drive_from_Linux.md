---
title: "Can't see GPT hard drive from Linux?"
date: 2011-11-07
forum: General Help
---

### Post by mace2 on 2011-11-07
Hi, I've tried searching but I am getting lost because I am not too familiar with this stuff.

I am trying to access a 2TB internal hard drive I have in 11.04. It is GPT (works fine in Windows 7), and is sda1 in the list.

Here is fdisk -l:
```

[~] $ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000394706432 bytes
256 heads, 63 sectors/track, 242250 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d9e0b3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      266306  2147483647+  ee  GPT

Disk /dev/sdb: 640.1 GB, 640133946880 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97749774

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       31932   256387072    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           31932       77826   368638977    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sdb5           31932       75880   353013760   83  Linux
/dev/sdb6           75881       77826    15624192   82  Linux swap / Solaris

```

I tried looking up GNU Parted but that only seems to be a way to repartition the drive... is there no way I can mount it as it is? If I have to I can back it up to an external and repartition it, but I would prefer not to.

Thanks!

---

### Post by searchfgold6789 on 2011-11-07
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.It looks like you'll have to back it up and repartition using GParted.

---

### Post by mace2 on 2011-11-07
> **searchfgold6789 said:**
> It looks like you'll have to back it up and repartition using GParted.

If I do this will I be able to access the drive with Windows still? Thanks.

---

### Post by mjuhasz on 2011-11-07
The fdisk utility does not support GPT hence the error messsage. Just do what the message says: use parted, a very sophisticated utility. If it's too much for you, use a frontend like gparted.

Linux handles GPT partition tables just fine. No need to repartition the drive (which means losing all your data on it).
MBR is the legacy and GPT is the (not so) new way of partitioning. MBR has a lot of limitations that GPT has finally overcome.

---

### Post by searchfgold6789 on 2011-11-07
> **mace2 said:**
> If I do this will I be able to access the drive with Windows still? Thanks.
Yup, but you may have to repair the filesystem first using the Windows install CD or a separate Windows installation. Then it'll work just dandy.
 - search
P.S. As mjuhasz said, Linux will detect and mount your partition but to use fdisk on it you need to use GParted. Don't do any of this if you're playing with your Windows system partition!!! Instead just try to mount it.

---

### Post by oldfred on 2011-11-07
I have gpt on two of my 4 drives. And I have no issues related to gpt. Every partition looks like everyone else. I did have an issue booting XP from gpt boot drive, several versions ago, but that has long since been fixed. I am primarily booting with Maverick on gpt.

So is the issue, just that you have not mounted the partition(s) and given yourself permissions?

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by mace2 on 2011-11-07
> **oldfred said:**
> I have gpt on two of my 4 drives. And I have no issues related to gpt. Every partition looks like everyone else. I did have an issue booting XP from gpt boot drive, several versions ago, but that has long since been fixed. I am primarily booting with Maverick on gpt.

So is the issue, just that you have not mounted the partition(s) and given yourself permissions?

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thank you for the links. I tried but I'm not really getting anywhere. I guess the problem is permissions?

The HDD is not listed in fstab.
```
[~] $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=805d7d1f-676e-4755-a704-352d4b74c435 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dfbb3954-f3ff-482d-8347-ca28508fe57b none            swap    sw              0       0
[~] $ 

```

I also can't seem to mount it directly. It asks for a filesystem type...
```
[~] $ sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type
[~] $ 
[~] $ sudo mount -t ntfs /dev/sda1 /mnt
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[~] $ 

```

I tried GPT as a type but it didn't recognize that. I guess GPT is something that goes on the filesystem (like NTFS etc?). Sorry I'm pretty new to a lot of this.

---

### Post by WorMzy on 2011-11-07
What does parted say about the disk?

```
sudo parted -l
```

I use GPT on my system with no problems.

---

### Post by oldfred on 2011-11-07
Gpt(GUID) & MBR(msdos) are partitioning schemes. NTFS & FAT32 for Windows or  ext3, ext4 etc for Linux are formats of the partitions.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Post this to show partitions.
$ sudo parted /dev/sda unit s print

A very large drive should not be formated as one partition unless you have another very large drive to back up to. Also the larger the partition the longer chkdsk will take. With NTFS you will have to manually run chkdsk every 40 odd boots where Ubuntu runs fsck automatically on Linux formats.

---

### Post by mace2 on 2011-11-07
Here is the output, oldfred.
```
[~] $ sudo parted /dev/sda unit s print
Error: Can't have a partition outside the disk!                  
```

Here is parted -l.
```
[~] $ sudo parted -l
Error: Can't have a partition outside the disk!                           

Model: ATA WDC WD6401AALS-0 (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   263GB  263GB   primary   ntfs
 3      263GB   640GB  377GB   extended
 5      263GB   624GB  361GB   logical   ext4
 6      624GB   640GB  16.0GB  logical   linux-swap(v1)


[~] $ 

```

I noticed in gparted it says my 2TB drive is "unallocated," yet it is operating normally in Windows. I am confused about how fdisk -l notices the drive but parted does not.

---

### Post by oldfred on 2011-11-07
Parted is saying it is mis-partiitoned. Is it really gpt? With 2TB it can be either gpt or MBR as 2TiB or about 2.2GB can still be MBR.

Do this and save partssda.txt to your sdb or a flash drive:
sudo sfdisk -d /dev/sda > partssda.txt

Then post partssda.txt output.


Download and run this program. Post the results of the p command.

Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by mace2 on 2011-11-07
Here is the partssda.txt file:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        1, size=4294967295, Id=ee
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0

```

Here is what fixparts tells me when I try to run it (before I can use 'p' as per the tutorial):
```
[~] $ sudo fixparts /dev/sda
FixParts 0.8.0

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!

[~] $ 
[~] $ sudo fixparts /dev/sda1
FixParts 0.8.0

Loading MBR data from /dev/sda1

Unable to read MBR data from '/dev/sda1'! Exiting!


```
Would it help If I went into Windows and got information about the filesystem? I thought it was GPT though..

Thanks for your continued help! Much appreciated.

---

### Post by oldfred on 2011-11-07
My concern is if sda1 is beyond the end of the drive. I was hoping fixparts would see that and correct it.

Download gdisk either from synaptic or the newer version from rodbooks.com.

My gdisk output you can see the last partition end is inside the end of the drive:

```
fred@fred-MavericDT:~$ sudo gdisk /dev/sdc -l
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: [COLOR=Red]312581808[/COLOR] sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8309E92E-0149-4DB4-9AF3-AA60B26ED1D1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 1-sector boundaries
Total free space is 5070 sectors (2.5 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34           16064   7.8 MiB     EF02  
   2           16065        51215219   24.4 GiB    0700  MAVERICK
   3        51215220        57352049   2.9 GiB     8200  
   4        57352050       [COLOR=Red]312576704  [/COLOR] 121.7 GiB   0700  

```

---

### Post by mace2 on 2011-11-08
Huh, it seems the partition ends outside the drive... what does this mean?

```
[~] $ sudo gdisk /dev/sda -l
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
8114 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 3907020911 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 87EA4D52-1FE4-49C4-BE34-6E0C9B0A6D62
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907020877
Partitions will be aligned on 8-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      3907028991   1.8 TiB     0700  Basic data partition
[~] $ 
[~] $ 

```

---

### Post by oldfred on 2011-11-08
We have seen cases where both Microsoft & Testdisk have written extended partition in MBR partitioning beyond the end. I have not seen it with gpt.

I have always used gparted on my gpt disks and never had a problem. I was hoping the fixparts program would see the issue and rewrite the partition table correctly. I think you will have to to it with gdisk but I am not any more familar with the details of using gdisk than you are. But the rodbooks site has some good instructions on gdisk as well.

I would use gdisk to shrink sda2 by a small amount.

Update 
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

I would suggest the binary backup and a text file copy of the current partition table. Then you can see what gdisk says about partition table.

---

### Post by mace2 on 2011-11-08
Thanks for your help oldfred. I just got in after a long day. I think I will try to resize the partition to the end of the disk and see what happens. I have made a backup of the drive in case things go poorly.

I will make an update (and tag the thread) if it works correctly.

For the record, here is what gdisk tells me about the partition table:
> [~] $ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
8114 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): p
Disk /dev/sda: 3907020911 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 87EA4D52-1FE4-49C4-BE34-6E0C9B0A6D62
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907020877
Partitions will be aligned on 8-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      3907028991   1.8 TiB     0700  Basic data partition

Command (? for help): 


---

