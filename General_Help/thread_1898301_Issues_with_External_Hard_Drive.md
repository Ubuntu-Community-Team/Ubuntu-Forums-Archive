---
title: "Issues with External Hard Drive"
date: 2011-12-21
forum: General Help
---

### Post by AlexOnVinyl on 2011-12-21
Hi,

My computer decided to crash when I was copying files to my ntfs external - tried to revive it, used ntfsfix for it, then received some error code about mounting it again, error mounting code 1 - then went into Storage Device Manager, manually re-mounted it, now its giving me bs about a whole other harddrive being mounted so I have 2 instances of the same drive.

Looks like this - photo attached, please save me before I decide to throw my computer out the window.


Here's the dialogue from the fdisk:


Disk /dev/sdb1: 967.5 GB, 967497511424 bytes
255 heads, 63 sectors/track, 117624 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/sdb1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by kg.korelin on 2011-12-21
If i get it correct, the output of mount command shows you, that your device is mounted on two different mounting points. If so, do sudo umount /your/mountin/point/ (for mountin point, which is actually empty), but not sudo umount /dev/sdXn.

---

### Post by AlexOnVinyl on 2011-12-21
> **kg.korelin said:**
> If i get it correct, the output of mount command shows you, that your device is mounted on two different mounting points. If so, do sudo umount /your/mountin/point/ (for mountin point, which is actually empty), but not sudo umount /dev/sdXn.

Thats the thing, when I try to find the mount point it shows nothing...

---

### Post by AlexOnVinyl on 2011-12-21
> **kg.korelin said:**
> If i get it correct, the output of mount command shows you, that your device is mounted on two different mounting points. If so, do sudo umount /your/mountin/point/ (for mountin point, which is actually empty), but not sudo umount /dev/sdXn.

Here's what's going on.


[http://www.youtube.com/watch?v=sC32AKsAF-Y]("http://www.youtube.com/watch?v=sC32AKsAF-Y")

---

### Post by kg.korelin on 2011-12-21
Can you type "mount" in terminal and show us the output?

---

### Post by BC59 on 2011-12-21
The best guide for issues like this is [here]("http://ubuntuforums.org/showthread.php?t=283131")

In any case you can check the fstab of the drive and post it here.

```
sudo gedit /etc/fstab
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> The best guide for issues like this is [here]("http://ubuntuforums.org/showthread.php?t=283131")

In any case you can check the fstab of the drive and post it here.

```
sudo gedit /etc/fstab
```

here's the output

```
proc                                       /proc              proc     nodev,noexec,nosuid                0  0  
UUID=10f5c70b-c8d5-4e31-9645-7ce221a9861f  /                  ext4     errors=remount-ro                  0  1  
UUID=01CBA47F9A3668D0                      /media/ALEXPOULOS  ntfs-3g  defaults,users,locale=en_US.UTF-8  0  0  
UUID=837d7d98-b99b-4a8a-9e8f-5603bd9aa5f3  none               swap     sw                                 0  0  
```

---

### Post by AlexOnVinyl on 2011-12-21
> **kg.korelin said:**
> Can you type "mount" in terminal and show us the output?

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/alex/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alex)
/dev/sdb2 on /media/FAT32 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1 on /media/ALEXPOULOS type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by BC59 on 2011-12-21
> **AlexOnVinyl said:**
> here's the output

```
proc                                       /proc              proc     nodev,noexec,nosuid                0  0  
UUID=10f5c70b-c8d5-4e31-9645-7ce221a9861f  /                  ext4     errors=remount-ro                  0  1  
UUID=01CBA47F9A3668D0                      /media/ALEXPOULOS  ntfs-3g  defaults,users,locale=en_US.UTF-8  0  0  
UUID=837d7d98-b99b-4a8a-9e8f-5603bd9aa5f3  none               swap     sw                                 0  0  
```

Try this, edit the fstab
```
sudo gedit /etc/fstab
``` and comment with hash# in front of the drive settings. Then unmount unplug and plug again.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Try this, edit the fstab
```
sudo gedit /etc/fstab
``` and comment with hash# in front of the drive settings. Then unmount unplug and plug again.

what do you want me to comment?

here's the photo:

---

### Post by BC59 on 2011-12-21
# UUID=01CBA47F9A3668D0                      /media/ALEXPOULOS  ntfs-3g  
# defaults,users,locale=en_US.UTF-8  0  0 

Comment with hash (#) in front of the lines in order to deny the reading of the lines.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> # UUID=01CBA47F9A3668D0                      /media/ALEXPOULOS  ntfs-3g  
# defaults,users,locale=en_US.UTF-8  0  0 

Comment with hash (#) in front of the lines in order to deny the reading of the lines.

How will this fix my issue? I originally had a corrupt drive because of copying files over to my ntfs - then I ran ntfsfix /dev/sdb1 - and it fixed it, I can read the files, but sometimes it gives me an error code of "failure to mount error code 1" - so I went into System>Administration>Storage Device Manager and pressed mount while it was already mounted and got stuck with that extra dupe of my external.

for future reference, how would I fix a corrupted external ntfs drive on LINUX, because all the people on the IRC kept telling me it was impossible and told me to load windows...

---

### Post by BC59 on 2011-12-21
You have to repair the problems created from Storage Device Manager. SDM is writing on your fstab. So if you delete the entry in fstab you repair the problem. Katalaves;

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> You have to repair the problems created from Storage Device Manager. SDM is writing on your fstab. So if you delete the entry in fstab you repair the problem. Katalaves;

So nothing I did is anything completely damaged?

The Fstab isnt a huge critical part?

Im sorry, Im rather new to linux

---

### Post by BC59 on 2011-12-21
fstab is a configuration file. You can edit it with a text editor.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> fstab is a configuration file. You can edit it with a text editor.

so, what i did in the fstab was to undo the damage I did in the storage manager?  is there anything more I need to do?

---

### Post by BC59 on 2011-12-21
It's not a damage, it's a wrong entry.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> It's not a damage, it's a wrong entry.

alright.


so what about fixing my external being corrupt? just use ntfsfix?

---

### Post by BC59 on 2011-12-21
The best way to fix a hard drive is using Windows tools. You could plug it in a Windows computer and format it.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> The best way to fix a hard drive is using Windows tools. You could plug it in a Windows computer and format it.

ok, but I need it repaired, not formatted because I have years, years and years of music and media on it.

---

### Post by BC59 on 2011-12-21
I'm afraid there is no solution other but format it. You cannot avoid it. It's the best way to solve the problems of a HDD and repair any bad sectors. All other solutions are imperfect.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> I'm afraid there is no solution other but format it. You cannot avoid it. It's the best way to solve the problems of a HDD and repair any bad sectors. All other solutions are imperfect.

Now its giving me this error when I unplug it:

```
umount: /media/ALEXPOULOS is not in the fstab (and you are not root)
```

---

### Post by BC59 on 2011-12-21
Now you can open Storage Device Manager and set the options to default.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Now you can open Storage Device Manager and set the options to default.

alright, now I'm getting this:

2 media folders for the same device.




----
---- Also! now its making me re-setup sdb1

---

### Post by BC59 on 2011-12-21
> **AlexOnVinyl said:**
> alright, now I'm getting this:

2 media folders for the same device.




----
---- Also! now its making me re-setup sdb1

Yes, choose Ok to reconfigure. Then set the options to default.

---

### Post by BC59 on 2011-12-21
If you go to File System--media what is inside the folder of media?

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Yes, choose Ok to reconfigure. Then set the options to default.

Ok done.


> **BC59 said:**
> If you go to File System--media what is inside the folder of media?

ALEXPOULOS, ALEXPOULOS_, FAT32, sdb1

---

### Post by BC59 on 2011-12-21
Then try this. 

Unplug the external Hard drive.

Then run:

```
gksudo nautilus
```

From the root nautilus now, go to files system--media and delete all the folders. Ensure that you don't have plugged another external drive.

Then exit and check if the external drive can be plugged correctly.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Then try this. 

Unplug the external Hard drive.

Then run:

```
gksudo nautilus
```

From the root nautilus now, go to files system--media and delete all the folders. Ensure that you don't have plugged another external drive.

Then exit and check if the external drive can be plugged correctly.

Alright, my FAT32 plugged in fine, but my NTFS got this:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sdb1

---

### Post by BC59 on 2011-12-21
Mount the HDD with this

```
sudo umount /dev/sdb1
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Mount the HDD with this

```
sudo umount /dev/sdb1
```

but its not the HDD its the external

---

### Post by BC59 on 2011-12-21
> **AlexOnVinyl said:**
> Alright, my FAT32 plugged in fine, but my NTFS got this:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/sdb1

As you see above you intent to mount the sdb1.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> As you see above you intent to mount the sdb1.

umount: /dev/sdb1: not mounted

.....
what next?:(

---

### Post by BC59 on 2011-12-21
> **AlexOnVinyl said:**
> umount: /dev/sdb1: not mounted

.....
what next?:(

```
sudo mount /dev/sdb1 /mnt
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> ```
sudo mount /dev/sdb1 /mnt
```

alright, mounted, but the NTFS Partition on the external didnt mount... just the FAT partition

---

### Post by BC59 on 2011-12-21
Do the same for the other partition
```

sudo mount /dev/sda2 /mnt
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> ```
sudo mount /dev/sdb1 /mnt
```

I found this:


File system>MNT>and it shows the directories of my External, except doesnt show my external in the computer section..

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Do the same for the other partition
```

sudo mount /dev/sda2 /mnt
```

mount: you must specify the filesystem type

---

### Post by BC59 on 2011-12-21
> **AlexOnVinyl said:**
> mount: you must specify the filesystem type

Sorry should be

```
sudo mount /dev/sdb2 /mnt
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Sorry should be

```
sudo mount /dev/sdb2 /mnt
```

ok, we just mounted my other partition, now what about the NTFS?

---

### Post by BC59 on 2011-12-21
Can you post the results of these commands?

```
sudo parted /dev/sda print

sudo fdisk -l
```

---

### Post by BC59 on 2011-12-21
and this

```
sudo parted /dev/sdb print
```

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> and this

```
sudo parted /dev/sdb print
```

```
alex@griever:~$ sudo parted /dev/sda print
Model: ATA Hitachi HTS54501 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  157GB  157GB   primary   ext4            boot
 2      157GB   160GB  2950MB  extended
 5      157GB   160GB  2950MB  logical   linux-swap(v1)

alex@griever:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000deca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19099   153407488   83  Linux
/dev/sda2           19099       19458     2880513    5  Extended
/dev/sda5           19099       19458     2880512   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021631

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      117625   944821788+   7  HPFS/NTFS
/dev/sdb2          117626      121600    31929187+   c  W95 FAT32 (LBA)
alex@griever:~$ sudo parted /dev/sdb print
Model: WD Elements 1023 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  967GB   967GB   primary  ntfs
 2      967GB   1000GB  32.7GB  primary  fat32        lba

alex@griever:~$ 

```

---

### Post by BC59 on 2011-12-21
Everything looks ok. Are you sure that you cannot see the external disc? Plug it and unplug it, but before to unplug it do a right click and unmount.

---

### Post by AlexOnVinyl on 2011-12-21
> **BC59 said:**
> Everything looks ok. Are you sure that you cannot see the external disc? Plug it and unplug it, but before to unplug it do a right click and unmount.

I can't see my other External Partition, the NTFS, only the Fat32

---

### Post by AlexOnVinyl on 2011-12-21
> **bc59 said:**
> everything looks ok. Are you sure that you cannot see the external disc? Plug it and unplug it, but before to unplug it do a right click and unmount.
oh scratch that!!!! I see it now!!!! Thank you>! You fixed it!!!!! Thank you for your time so much!!!!!!!!!!!!!!!!!!

You saved me!!!!!!!

---

### Post by BC59 on 2011-12-21
Glad to help.
Please mark the thread as solved from the Thread tools close to the top.

---

