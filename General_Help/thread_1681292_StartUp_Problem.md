---
title: "StartUp Problem"
date: 2011-02-03
forum: General Help
---

### Post by TopEnder on 2011-02-03
G'Day All and Thanks in Advance,

I had my /home partition on a seperate HDD,  had problems with this Drive indications it was failing so I copied the /home partition to my Ubuntu HDD by using Gparted.
[IMG]/home/smokey/Desktop/Gparted.png[/IMG]  -  [COLOR="Blue"]forgot how to insert a image, but basically /dev/sdc5 appears to be a sub partition of /dev/scd4[/COLOR]

The problem I getting now is when I startup, I get a message "Press S to skip mounting or M for manual recovery", I then press S and all apears normal able to access both Ubuntu & Vista Drives & Files.  Is there anyway I can move the /home partition from /dev/sdc5 (/home) (it appaers to be a sup-partition of sdc4) to /dev/sdc4 and remove the /dev/sdc5 sup-partiton or do I need to wait until I reinstall or  install a newer version of Ubuntu. I have attached the following hoping it can help in solving both problems:

fdisk -l
cat /etc/fstab
blkid

```
smokey@smokey-lynix:~$ sudo fdisk -l
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6767f78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10011    80413326   83  Linux

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5c0e5fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7180    57673318+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff0a13ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2611    20972826   83  Linux
/dev/sdc2            2612        2872     2096482+  82  Linux swap / Solaris
/dev/sdc3            2873       12956    80999730   83  Linux
/dev/sdc4           12957       19458    52220929    5  Extended
/dev/sdc5           12957       19458    52220928   83  Linux

```

```
smokey@smokey-lynix:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#
#Entry for /dev/sdc1 
UUID=aaff4197-b07e-4d1a-bf2f-e7f76c8a3719	/	reiserfs	notail	0	1
#
#Entry for /dev/sdc5 :
UUID=5001c147-aac5-45aa-977b-b104bd1058af	/home	reiserfs	defaults	0	2
#Entry for /dev/sdc3 :
UUID=13522191-ad99-42f9-a5d5-693873021c9c	/media/Ubuntu-Files	ext4	defaults	0	2
#
#Entry for /dev/sdb1 :
UUID=D494B9E194B9C670	/media/Vista	ntfs-3g	defaults,locale=en_AU.utf8	0	0
#Entry for /dev/sda1 :
UUID=54b5e7c1-c802-422b-9bd3-7c30138d0b1c	/media/Working	xfs	defaults	0	2
#
#Entry for /dev/sdc2 :
UUID=72abf8fc-d469-49c1-ba56-041ac6c14707	none	swap	sw	0	0
#
/dev/fd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0
sudo mount -a

```

```
smokey@smokey-lynix:~$ sudo blkid
/dev/sda1: LABEL="Working" UUID="54b5e7c1-c802-422b-9bd3-7c30138d0b1c" TYPE="xfs" 
/dev/sdb1: UUID="D494B9E194B9C670" TYPE="ntfs" 
/dev/sdc1: UUID="aaff4197-b07e-4d1a-bf2f-e7f76c8a3719" TYPE="reiserfs" 
/dev/sdc2: UUID="72abf8fc-d469-49c1-ba56-041ac6c14707" TYPE="swap" 
/dev/sdc3: LABEL="Ubuntu-Files" UUID="13522191-ad99-42f9-a5d5-693873021c9c" TYPE="ext4" 
/dev/sdc5: UUID="5001c147-aac5-45aa-977b-b104bd1058af" TYPE="reiserfs" 

```
Thanks, TopEnder

---

### Post by Brandon Williams on 2011-02-05
A disk is only allowed to have 4 primary partitions, one of which can be an extended partition that contains multiple secondary partitions. In your case, /dev/sdc4 is an extended partition and /dev/sdc5 is a secondary partition.

Since you only have the one secondary partition, you could convert /dev/sdc4 into a standard primary partition and copy the data from /dev/sdc5 over to your reconfigured /dev/sdc4. You would have to copy everything off of /dev/sdc5 first and then use a repartitioning tool to delete the existing /dev/sdc5 and change the partition type of /dev/sdc4. After that, format the filesystem on /dev/sdc4 and copy the old /dev/sdc5 data onto it.

I don't recommend that you do any of this, since there's always a risk that you will lose the data from /dev/sdc5 in the process, as well as the risk that you will accidentally destroy one of the other partitions on /dev/sdc. Having an extended partition doesn't waste any significant amount of disk space, and having it allows for the possibility of adding partitions in the future if you so desire.

---

### Post by TopEnder on 2011-02-05
Brandon,   Thanks for your reply and information I will consider it but will probable waituntil I either update or install a fresh new installation.  TopEnder
> **Brandon Williams said:**
> A disk is only allowed to have 4 primary partitions, one of which can be an extended partition that contains multiple secondary partitions. In your case, /dev/sdc4 is an extended partition and /dev/sdc5 is a secondary partition.

Since you only have the one secondary partition, you could convert /dev/sdc4 into a standard primary partition and copy the data from /dev/sdc5 over to your reconfigured /dev/sdc4. You would have to copy everything off of /dev/sdc5 first and then use a repartitioning tool to delete the existing /dev/sdc5 and change the partition type of /dev/sdc4. After that, format the filesystem on /dev/sdc4 and copy the old /dev/sdc5 data onto it.

I don't recommend that you do any of this, since there's always a risk that you will lose the data from /dev/sdc5 in the process, as well as the risk that you will accidentally destroy one of the other partitions on /dev/sdc. Having an extended partition doesn't waste any significant amount of disk space, and having it allows for the possibility of adding partitions in the future if you so desire.

---

