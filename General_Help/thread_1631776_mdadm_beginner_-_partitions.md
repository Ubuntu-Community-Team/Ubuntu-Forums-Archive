---
title: "mdadm beginner - partitions"
date: 2010-11-27
forum: General Help
---

### Post by Nanyak on 2010-11-27
Hi all,
 
Just bought two new 2tb hard drives that I want to run in a raid1 config using mdadm, in my Ubuntu Server 10.04. 
 
I have read several guides on the internet and think I have my head around most of it. 
 
The process I am going to follow is listed below (I have posted the actual fdisk output from my server there). _Can you guys see anything wrong in what I am doing?_
 
I am stuck with partitions. I do not want to have just a 2tb disk sitting there, I would prefer to partition it, so that I can allocate space to different things, e.g. backup, mail server etc. etc. 
 
_So basically, I am just trying to find out how to modify my approach below to create a 2tb partition HDD in a raid1? _For e.g. I want to partition my 2tb hard drive into 4 partitions and then raid1 it. 
 
Thanks for any help and advice. I have done a lot of reading, but struggling to get my head around this simple bit. 
 
**[SIZE=3][FONT=Calibri]> sudo fdisk -l[/FONT][/SIZE]**
> 
 
[SIZE=3][FONT=Calibri]Disk /dev/sda: 2000.4 GB, 2000398934016 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]255 heads, 63 sectors/track, 243201 cylinders[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Disk identifier: 0x00000000[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Disk /dev/sda doesn't contain a valid partition table[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]255 heads, 63 sectors/track, 243201 cylinders[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Disk identifier: 0x00000000[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Disk /dev/sdb doesn't contain a valid partition table[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]Disk /dev/sdc: 500.1 GB, 500107862016 bytes[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]255 heads, 63 sectors/track, 60801 cylinders[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Disk identifier: 0x000f0b8b[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Device Boot Start End Blocks Id System[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]/dev/sdc1 * 1 32 248832 83 Linux[/FONT][/SIZE]
[FONT=Calibri][SIZE=3]Partition 1 does not end on cylinder boundary.[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]/dev/sdc2 32 60802 488135681 5 Extended[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]/dev/sdc5 32 60802 488135680 8e Linux LVM[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]**[Quote]sudo fdisk /dev/sda**[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]sudo fdisk /dev/sda[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]n (for new partition)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]p (for primary partition)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]1 (partition number 1)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri][use default values for first and last cylinder][/FONT][/SIZE]
[SIZE=3][FONT=Calibri]t (selection partition 1)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]HEX code (type L to list codes): fd[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]w (to save changes)[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]**> sudo fdisk /dev/sdb**[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]n (for new partition)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]p (for primary partition)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]1 (partition number 1)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri][use default values for first and last cylinder][/FONT][/SIZE]
[SIZE=3][FONT=Calibri]t (selection partition 1)[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]HEX code (type L to list codes): fd[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]w (to save changes)[/FONT][/SIZE]
 
[FONT=Calibri][SIZE=3]**> sudo mdadm –create /dev/md0 --levl=1 –raid-devices=2 /dev/sda /dev/sdb**[/SIZE][/FONT]
[/Quote]

---

