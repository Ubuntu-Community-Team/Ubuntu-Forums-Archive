---
title: "Self Inflicted Error in Installing Ubuntu"
date: 2010-06-11
forum: General Help
---

### Post by mazria on 2010-06-11
[SIZE=2]I need help, please. This appears to be a variation on a theme – other people having similar problems[/SIZE]
 [SIZE=2]Seeking a solution to the problems I inflicted upon my operating system.[/SIZE]
 [SIZE=2]First I must say that I have no experience what so ever in Linux.  Installed OS 4 days ago and have been reading about how to repair it for the last 3 days.  The machine is used primarily for working in photography programs.  The hope was to be able to access and use some of the programs available in Linux for photography and 3D illustration.[/SIZE]
 [SIZE=2]Loaded Karmic and immediately upgraded to 10.04.[/SIZE]
 [SIZE=2]When checking my partitions in XP Pro it was noticed that ~73.8 GB (sda6) of partition space appeared to have been lost when installing Ubuntu.  Using EZ GIG in XP I re-formatted the region (sda6) that appeared to have been rendered useless, without knowledge of the pending consequence. There are now more partitions on the hard drive than was ever intended, but may be found useful.   Windows XP resides in sda1. Stored XP OS images in sda2.  sda 8 is empty – not placed into service to date. I use sda9 for processing and storage of  photography work (no photos there now – all moved to external HD).  Windows page file stored on small partition on external HD.  sda5, sda6 & sda7 were previously a single partition.[/SIZE]
 [SIZE=2]Have been getting the “grub rescue>” prompt since the reboot after re-formatting.[/SIZE]
 [SIZE=2]My attempts at reinstalling Grub2 were unsuccessful as can be seen.[/SIZE]
 [SIZE=2]Is reinstalling Ubuntu automatically (sudo dpkg-reconfigure -phigh -a) an option? (a reasonable option?)[/SIZE]
 

 [SIZE=2]Attached is a copy of  the attempts made.[/SIZE]
 

 [SIZE=2]To run a command as administrator (user "root"), use "sudo <command>".[/SIZE]
 [SIZE=2]See "man sudo_root" for details.[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount/dev/sda6/mnt[/SIZE]
 [SIZE=2]sudo: mount/dev/sda6/mnt: command not found[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/dev/sda6/mnt[/SIZE]
 [SIZE=2]mount: can't find /dev/dev/sda6/mnt in /etc/fstab or /etc/mtab[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo fdisk -l[/SIZE]
 [SIZE=2]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/SIZE]
 [SIZE=2]255 heads, 63 sectors/track, 60801 cylinders[/SIZE]
 [SIZE=2]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE]
 [SIZE=2]Disk identifier: 0x249e249d[/SIZE]
    [SIZE=2]Device Boot      Start         End      Blocks   Id  System[/SIZE][SIZE=2][/SIZE]
 [SIZE=2]/dev/sda1   *           1       15936   128005888+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]/dev/sda2           15937       21673    46082452+   7  HPFS/NTFS  -Stored OS images for XP  [/SIZE] 
 [SIZE=2]/dev/sda3           21674       60801   314295660    f  W95 Ext'd (LBA)[/SIZE]
 [SIZE=2]/dev/sda5           21674       30911    74204203+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]/dev/sda6           30912       40547    77401138+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]/dev/sda7           40548       40962     3333456   82  Linux swap / Solaris[/SIZE]
 [SIZE=2]/dev/sda8           40963       47449    52106796    7  HPFS/NTFS[/SIZE]
 [SIZE=2]/dev/sda9           47450       60801   107249908+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]Disk /dev/sdb: 120.0 GB, 120034123776 bytesGRUB2 problem - 06-10-2010 for forum[/SIZE]
 [SIZE=2]255 heads, 63 sectors/track, 14593 cylinders[/SIZE]
 [SIZE=2]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE]
 [SIZE=2]Disk identifier: 0x8922059d[/SIZE]
   [SIZE=2]Device Boot      Start         End      Blocks   Id  System[/SIZE][SIZE=2][/SIZE]
 [SIZE=2]/dev/sdb1               1        1020     8193118+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]/dev/sdb2            1021       14593   109025122+   7  HPFS/NTFS[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/sda7/mnt[/SIZE]
 [SIZE=2]mount: can't find /dev/sda7/mnt in /etc/fstab or /etc/mtab[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt[/SIZE]
 [SIZE=2]mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/sda2/mnt[/SIZE]
 [SIZE=2]mount: can't find /dev/sda2/mnt in /etc/fstab or /etc/mtab[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt[/SIZE]
 [SIZE=2]ubuntu@ubuntu:~$ sudo mount --[/SIZE]
 

 

 [SIZE=2]When checking System Volume Information I found the following three files:[/SIZE]
 
[LIST=1]
[*][SIZE=2]Mount 	Point Manager [/SIZE] 	
[*][SIZE=2]_restore{2995D659-FAE8-40D6-808F-737C7F2511DE}[/SIZE]
[*][SIZE=2]Tracking 	Log[/SIZE]
[/LIST]
 

 

 

 [SIZE=2]Any help will be greatly appreciated![/SIZE]

---

### Post by Bucky Ball on 2010-06-11
```
[SIZE=2]/dev/sda7           40548       40962     3333456   82  Linux swap / Solaris[/SIZE]
```That seems to be your only Linux partition; a swap file. Where exactly do you have Ubuntu installed??

Best bet? When you get to the partitioning part of the installation, go 'Manual Partitioning' and put Ubuntu on the right partition.

To look around, Live CD, System->Administration->Partition Editor.

I would go back to square one and plan this on a piece of paper before getting in and deleting/creating partitions. Make a clear plan. Back everything up if you haven't already. Take note of where your Windows installation is before manual partitioning. Know what existing partition you are going put Ubuntu on, or decide whether you need to create one. If the latter, make sure you have the free space or a spare partition.

Good luck.

---

