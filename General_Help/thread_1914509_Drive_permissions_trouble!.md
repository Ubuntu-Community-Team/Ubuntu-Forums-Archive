---
title: "Drive permissions trouble!"
date: 2012-01-24
forum: General Help
---

### Post by che47audio on 2012-01-24
Hi there.
I have ubuntu 11.10 installed on a 160gb sata and a second sata of 1tb. This second drive is what I keep all of my media on, i.e music etc. For some reason in Ubuntu I do not appear to have write permissions to this drive, only read permissions. So when I try to copy files to the drive I get the error message "Error while copying. The folder "x" cannot be copied because you do not have permissions to create it in the destination."

Any advice would be greatly appreciated.

Thanks.

---

### Post by ajgreeny on 2012-01-24
Wow!  You waited _16 minutes_ and then complained that nobody answered.

No-one here is paid to do anything, so you must simply consider yourself lucky any time you do get an answer that helps, and please don't moan so quickly in future.

That is the end of my moan at you;  now to try to give you an answer.

How is the 1Tb disk formatted; ntfs?
Do you have ntfs3g installed?
Please show the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```
That may help sort out your problem.

---

### Post by che47audio on 2012-01-24
Thank you for your reply. Yes, in retrospect I was somewhat impatient. I just felt like I was doing something wrong when several threads that were 5 minutes younger than mine had already had over 200 views and mine hadn't had any?

The 1tb drive is formatted in FAT32.
I don't know if ntfs3g, how can I tell?
I should also mention that there is a 120gb sata drive installed, however the problem with the 1tb drive existed before and after this was installed.This 120gb drive works fine.

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea8f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            2048   312580095   156289024    5  Extended
/dev/sda5       306606080   312580095     2987008   82  Linux swap / Solaris
/dev/sda6            4096   306604031   153299968   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000476b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953375479   976687708+   b  W95 FAT32

Disk /dev/sdc: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfbe6fbe6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   234491903   117244928    b  W95 FAT32

Disk /dev/sdd: 2004 MB, 2004877312 bytes
64 heads, 18 sectors/track, 3399 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        3584     3915775     1956096    6  FAT16



and the fstab.......

cat /etc/fstab

UUID=394a9a41-303b-4c57-a355-1312701559fb swap swap sw 0 0
UUID=1b3826d3-e9a9-42c1-a3eb-53fb8b886c22 / ext4 defaults 0 1
UUID=F7F1-BBCC /home/chris/media vfat users 0 2


Thanks again, and apologies.

---

### Post by ajgreeny on 2012-01-25
As the disk is fat32, the ntfs3g question is superfluous; it is only needed for ntfs formatted partitions.  However you can easily see if it is installed from the software-center or synaptic if you have that installed.   I would also suggest that ntfs is a better filesystem for such a large disk/partition.

To get the 1TB fat32 disk mounted as read/write you will need to edit the fstab file.  First make a backup just in case it goes wrong with ```
sudo cp /etc/fstab /etc/fstab.bak
```
Now edit fstab with ```
gksudo gedit /etc/fstab
``` and change the third line you showed which I assume is the 1TB drive ```
UUID=F7F1-BBCC /home/chris/media vfat users 0 2
``` to ```
UUID=F7F1-BBCC /home/chris/media vfat defaults,user,dmask=027,fmask=137 0 0
```You should now be able to use the command ```
sudo mount -a
```and if no errors appear from that, you should be able to read/write to that disk.

---

### Post by che47audio on 2012-01-25
I followed your steps in backing up and editing the fstab.
Unfortunately when i ran the finally command:

sudo mount -a

I got "unable to resolve host"

Now when I try to open the drive I get
"You do not have the permissions necessary to view the contents of "media""

Thanks again

---

### Post by Morbius1 on 2012-01-25
> UUID=F7F1-BBCC /home/chris/media vfat defaults,user,dmask=027,fmask=137 0 0
Change "user" above to "uid=1000"
```
UUID=F7F1-BBCC /home/chris/media vfat defaults,uid=1000,dmask=027,fmask=137 0 0
```THen unmount the partition:
```
sudo umount /home/chris/media
```Then mount it again with the updated fstab:
```
sudo mount -a
```

---

### Post by che47audio on 2012-01-25
I followed these steps exactly and its seems to be working perfectly! Thankyou very much, this has made my year so far!

---

### Post by ajgreeny on 2012-01-25
> **Morbius1 said:**
> Change "user" above to "uid=1000"
```
UUID=F7F1-BBCC /home/chris/media vfat defaults,uid=1000,dmask=027,fmask=137 0 0
```THen unmount the partition:
```
sudo umount /home/chris/media
```Then mount it again with the updated fstab:
```
sudo mount -a
```
Very interesting!

I copied the fstab entry I gave for the OP from [https://help.ubuntu.com/community/Fstab#fat16_and_fat32](https://help.ubuntu.com/community/Fstab#fat16_and_fat32) so that obviously needs updating.  Glad I managed at least to get things moving.

Is this something new that has just not yet been changed in the community document?

---

### Post by Morbius1 on 2012-01-26
This forum seems to be preoccupied with the "user" option in fstab. Doing a "man mount" doesn't help either because it's misleading:
> **user **
  Allow an ordinary user to mount the filesystem.  The name of the mounting  user  is  written  to  mtab so that he can unmount the
filesystem again.
There is only one user at the moment fstab is executed at boot time and that is root. So this line:
>                               UUID=F7F1-BBCC /home/chris/media vfat defaults,user,dmask=027,fmask=137 0 0                      Will produce permissions of:
> drwxr-x--- root rootTotally inaccessible to anyone except root unless root later unmounts the partition.

One solution is to mount it with a specific user as owner with a "uid=xxxx" or specify all local users to have access with a "gid=46" and change the dmask / fmask to accommodate group access.

---

