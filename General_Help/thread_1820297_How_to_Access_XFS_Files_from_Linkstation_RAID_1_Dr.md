---
title: "How to Access XFS Files from Linkstation RAID 1 Drive"
date: 2011-08-07
forum: General Help
---

### Post by skj19 on 2011-08-07
[FONT=Arial][SIZE=2]I am trying to access files from one/both of two 1.5TB RAID 1 drives from my Buffalo Linkstation Pro Duo LS-W1.0TGL/R1 that no longer operates correctly (even after 2.5 hours trying every trick in the book with Buffalo tech support yesterday). I am new to Ubuntu & Linux so please pardon any dumb questions I ask.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Here's what I know:[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Files are in XFS format. When I attempt to access the drive the the ubuntu 11.04 GUI interface it shows the drive as "Array" and when I attempt to access it it says "unable to mount".[/SIZE][/FONT]

[FONT=Arial][SIZE=2]When I open a terminal window in ubuntu and run the command sudo fdisk -l I get the following response:[/SIZE][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]255 heads, 63 sectors/track, 182401 cylinders[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]Disk identifier: 0xd14f4adf[/FONT][/SIZE]
 
[SIZE=2][FONT=Times New Roman]Device Boot Start End Blocks Id System[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]/dev/sdb1 1 125 1004031 83 Linux[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]/dev/sdb2 126 748 5004247+ 83 Linux[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]/dev/sdb4 749 182401 1459127722+ 5 Extended[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]/dev/sdb5 749 873 1004031 82 Linux swap / Solaris[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]/dev/sdb6 874 182266 1457039241 83 Linux[/FONT][/SIZE]
[/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]The data I want is on partition /dev/sdb6 (I think). When I attempt to mount this partition (not sure if I'm doing this right) I get the following:[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]ubuntu@ubuntu:~$ sudo mkdir /mnt/point[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]ubuntu@ubuntu:~$ mount /dev/sdb6 /mnt/point[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt/point[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]**mount: unknown filesystem type 'linux_raid_member"**[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]To gather additional data I downloaded Gparted scanned the disk. It sees the following:[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/md125 (980MB, filesystem ext3)[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/md126 (980MB, filesystem linux-swap)[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/md127 (1.36TB, filesystem XFS)[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb (1.36TB, multiple filesystems)[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]_/dev/sdb breaks down as follows:_[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb1 ext3 size=980MB, used=132MB, unused=848MB[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb2 xfs size=4.77GB, used=269MB, unused=4.51GB[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb4 extended size=1.36GM[/SIZE][/FONT][/FONT][/FONT][FONT=Times New Roman]
[FONT=Times New Roman][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb5 linux-swap size=980MB[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2][FONT=Times New Roman][FONT=Arial][SIZE=2]/dev/sdb6 xfs size=1.36TB, used=774GB, unused=615GB[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]unallocated 1.0GB[/SIZE][/FONT][/FONT]
[FONT=Times New Roman][FONT=Arial][SIZE=2]unallocated unallocated 2.49MB[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]Note: the 774GB is the data I'm after.[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]So... can anyone help me get past the "linux_raid_member" error and mount my data so I can retrieve it and save it elsewhere?[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]Thanks,[/SIZE][/FONT][/FONT]

[FONT=Times New Roman][FONT=Arial][SIZE=2]Scott[/SIZE][/FONT][/FONT]
[/SIZE][/FONT][/FONT][/FONT][/FONT][/SIZE][/FONT][/FONT][/FONT][/FONT]

---

### Post by spammonster on 2011-09-21
Given the age of your post, I'm not sure if you already resolved this but just incase, I thought I would post.  I also have a Buffalo Linkstation Duo and I'm in the process of trying to upgrade the drive and encountered the same problem.  To access XFS volumes participating in a RAID use the following command:

mdadm --assemble --scan

From there you should be able to mount your volumes.  Out of curiosity have you tried doing a firmware upgrade to try and resurrect your Linkstation?  Good luck!

---

