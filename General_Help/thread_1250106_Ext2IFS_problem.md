---
title: "Ext2IFS problem"
date: 2009-08-26
forum: General Help
---

### Post by alimooghashang on 2009-08-26
Hi,
i have installed Ext2IFS, but i cant mount ubuntu volume in windows 7 7600.
what to do?
when i click on linux mounted drive , it says to format the drive.
what to do now?
thanks

---

### Post by danwood76 on 2009-08-26
What version of Ubuntu do you have?
In 9.04 you have the option to format as ETX4 which Ext2IFS doesnt support.

Also windows 7 support for Ext2IFS may be limited as MS block unsigned drivers from entering the OS.

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> What version of Ubuntu do you have?
In 9.04 you have the option to format as ETX4 which Ext2IFS doesnt support.

Also windows 7 support for Ext2IFS may be limited as MS block unsigned drivers from entering the OS.
i have 9.04
and the format is ext3

---

### Post by sefs on 2009-08-26
Is this a 1TB Drive?  I have a problem is Ext2IFS not mounting a 1TB drive but have not researched it yet to know why.

The other thing is if the drive was not cleanly dismounted in UBUNTU for example then it may not load under windows.  That means dismount it before you shutdown/plug out/ etc.  I am assuming its a external connected by USB?  You can click on the eject button to eject in nautilus then try load it up in windows after doing this and see what you get.

Is Ext2IFS compatible with windows 7 though?
Read this forum post...
[http://www.networkedmediatank.com/showthread.php?tid=23220](http://www.networkedmediatank.com/showthread.php?tid=23220)

---

### Post by alimooghashang on 2009-08-26
> **sefs said:**
> Is this a 1TB Drive?
no
i have 160 GB HDD on Hp Pavilion Laptop.
and also 10 gig is assosiated to ubuntu

---

### Post by danwood76 on 2009-08-26
I really dont think EXT2IFS is compatible with Windows 7.

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> I really dont think EXT2IFS is compatible with Windows 7.
no,
it works,
but the drive is wrong
and says i should format it
i don't know what to do.
it aslo doesn't work in XP and says to format it.

---

### Post by danwood76 on 2009-08-26
Well obvioulsy the driver isnt working?

Try ext2FSD and see if you get the same issue.
Are you 100% sure it is EXT3 and not EXT4?

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> well obvioulsy the driver isnt working?
Are you 100% sure it is ext3 and not ext4?

[attach]126310[/attach]

---

### Post by danwood76 on 2009-08-26
Can you boot to Ubuntu, mount the partition and give output of the following commands:
```

sudo fdisk -l
sudo mount

```

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> Can you boot to Ubuntu, mount the partition and give output of the following commands:
```

sudo fdisk -l
sudo mount

```
unfortunately , not now, cause the loading stops and the capslock light splash. and ubuntu won't boot.
i have this problem now.

---

### Post by alimooghashang on 2009-08-26
i have booted in live mode and the result is this.


```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7758e15e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7064    36258673+   7  HPFS/NTFS
/dev/sda6            7065       10198    25173823+   7  HPFS/NTFS
/dev/sda7           10199       14003    30563631    7  HPFS/NTFS
/dev/sda8           14004       17998    32089806    7  HPFS/NTFS
/dev/sda9           17999       18060      497983+  83  Linux
/dev/sda10          18061       18309     2000061   82  Linux swap / Solaris
/dev/sda11          18310       19457     9221278+  83  Linux

ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
ubuntu@ubuntu:~$ 



```

---

### Post by danwood76 on 2009-08-26
> **alimooghashang said:**
> unfortunately , not now, cause the loading stops and the capslock light splash. and ubuntu won't boot.
i have this problem now.

Right are you trying to boot off of the partition that wont mount using EXT2IFS?
Could you have a corrupt filesystem?

The output of the last command didnt help much as you hadn't mounted /dev/sda11.

Could you also try EXT2FSD to see if you have issues with that?

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> Right are you trying to boot off of the 
Could you also try EXT2FSD to see if you have issues with that?
Now, this opened the drive.
but every folder i try to open got an error.

```


I:\home Down refers to a location that is unavailable.
It could be on a hard drive on this computer, or on a network.
Check to make sure that the disk is properly inserted,
or that you are connected to the Internet or your network, 
and then try again. If it still cannot be located, 
the information might have been moved to a different location.

```

---

### Post by danwood76 on 2009-08-26
Load up a live CD and run a checkdisk on the partition.

```

sudo fsck -t ext3 /dev/sda11

```

I suspect there are some issues with the filesystem integrity causing your ubuntu not to boot and also your fs problems within windows.

---

### Post by Jose Catre-Vandis on 2009-08-26
See here:
[http://ubuntuforums.org/showthread.php?t=1234154](http://ubuntuforums.org/showthread.php?t=1234154)

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> Load up a live CD and run a checkdisk on the partition.

```

sudo fsck -t ext3 /dev/sda11

```I suspect there are some issues with the filesystem integrity causing your ubuntu not to boot and also your fs problems within windows.

Doesn't it hurt the files?
i need all of my files.
> ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sda11
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Group descriptors look bad... trying backup blocks...
Resize inode not valid.  Recreate<y>?

---

### Post by egalvan on 2009-08-26
> **alimooghashang said:**
> i have installed Ext2IFS, but cant mount ubuntu volume in windows 7 7600.
what to do?
when i click on linux mounted drive , **it says tit says to format the driveo format the drive**.
what to do now?
thanks


This is because the drive is probably formatted with large inodes.
per the Ext2IFS website, large inodes are NOT supported.
So Windows sees the drive as "not formatted".

>  Large inodes
The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them.

Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup. 

---

### Post by ExtremeCoolSha on 2009-08-26
As Danwood76 stated Ext2FSD is a better one to mount Linux volumes in the Windows. But there is a restriction in this. Note these softs can't mount Logical Volumes. Do u have any configured partitions in Ubuntu as a Logical Volume, or simply primary partitions ?

---

### Post by alimooghashang on 2009-08-26
> **ExtremeCoolSha said:**
> As Danwood76 stated Ext2FSD is a better one to mount Linux volumes in the Windows. But there is a restriction in this. Note these softs can't mount Logical Volumes. Do u have any configured partitions in Ubuntu as a Logical Volume, or simply primary partitions ?
i don't know what you mean.
but i have logical drives. and primery
as listed below:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7758e15e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7064    36258673+   7  HPFS/NTFS
/dev/sda6            7065       10198    25173823+   7  HPFS/NTFS
/dev/sda7           10199       14003    30563631    7  HPFS/NTFS
/dev/sda8           14004       17998    32089806    7  HPFS/NTFS
/dev/sda9           17999       18060      497983+  83  Linux
/dev/sda10          18061       18309     2000061   82  Linux swap / Solaris
/dev/sda11          18310       19457     9221278+  83  Linux


```

/dev/sda1 is primary, and /dev/sda5 - /dev/sda11 are logical (in windows. I don't know in ubuntu is the same or not)

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> Load up a live CD and run a checkdisk on the partition.

```

sudo fsck -t ext3 /dev/sda11

```

I suspect there are some issues with the filesystem integrity causing your ubuntu not to boot and also your fs problems within windows.
i also tried this.
but just this happened.
and so on.

```
ubuntu@ubuntu:~$ sudo fsck -t ext3 /dev/sda11
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Group descriptors look bad... trying backup blocks...
Resize inode not valid.  Recreate<y>? yes

/dev/sda11 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Group 0's inode table at 4 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 5 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 6 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 7 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 8 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 9 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 10 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 11 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 12 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 13 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 14 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 15 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 16 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 17 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 18 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 19 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 20 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 21 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 22 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 23 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 24 conflicts with some other fs block.
Relocate<y>? yes

Group 0's inode table at 25 conflicts with some other fs block.
Relocate<y>? 

```

---

### Post by danwood76 on 2009-08-26
You have some errors in the filesystem, this is probably why you cannot mount the partition and cannot boot from it.

If you can mount it under the live CD I would try and recover as much data as possible.

```

sudo mkdir /media/sda11
sudo mount /dev/sda11 /mount/sda11

```
Though the mount command will probably complain that the drive needs checking.

You can auto say yes to all the fixes fsck proposes this normally fixes the drive.

What did you do to the partition to get it in that state?

To say yes to all of fscks qs do the following:
```

sudo fsck -y -t ext3 /dev/sda11

```
Please be aware that you may loose some data doing this and if the drive is completely fubard then you wont recover anything.

What did you do to the partition to get it in that state?
Or is the drive bad?

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> 
What did you do to the partition to get it in that state?
Or is the drive bad?

i just have change the size of the partition in windows with partition manager :lolflag:

in linux , when i mount this volume, i got nothing appeared , but all of my data is in there due to the capacity of the volume i checked in properties.

---

### Post by danwood76 on 2009-08-26
Windows cannot resize linux partitions, it can barely resize windows partitions without issues.

If you have made the partition smaller you will have borked the partition and most probably lost your data. If you have made it bigger you will need to resize the ext volume within it.

There is a difference between resizing a partition and resizing the formatted volume within that partition. To resize a partition it takes 2 main steps which is automated in most partitoning software like Gparted.
Do not run a checkdisk on the volume as you will destroy the data if it is still there.

Can you describe what you have done with the (terrible) windows partitioner?

---

### Post by alimooghashang on 2009-08-26
> **danwood76 said:**
> Windows cannot resize linux partitions, it can barely resize windows partitions without issues.

If you have made the partition smaller you will have borked the partition and most probably lost your data. If you have made it bigger you will need to resize the ext volume within it.

There is a difference between resizing a partition and resizing the formatted volume within that partition. To resize a partition it takes 2 main steps which is automated in most partitoning software like Gparted.
Do not run a checkdisk on the volume as you will destroy the data if it is still there.

Can you describe what you have done with the (terrible) windows partitioner?
i have just resize the partiition, and reduce it smaller.
but i got the free space
and all the data are in volume but the capacity is smaller.

---

### Post by danwood76 on 2009-08-26
No you dont get what I mean.

Within the partition is a filesystem, windows **cannot** resize Linux EXT filesystems! By shrinking the partition you will break the filesystem and that is why you are having problems.

When a filesystem is created data can be placed at all points of the partition even at the end so by reducing its size before resizing the filesystem you will probably loose data.

Unfortunatly for you you didn't do any research on resizing linux partitions, I would be surprised if you can recover the partition and the filesystem.

To be able to resize an EXT filesystm you have to be able to run a clean fsck and fsck is likely to break the partition. You could repartition the drive back to how it was and recover that way if you are very lucky.

If there was nothing important on that partition I would just reformat the partition and start it again. Next time use the correct tool to resize like GParted.

---

### Post by alimooghashang on 2009-08-27
> **danwood76 said:**
> 
If there was nothing important on that partition I would just reformat the partition and start it again. Next time use the correct tool to resize like GParted.

I got what you mean.
yes , the data is so important for me 
i need to take them back or i will be killed :(( :(

---

### Post by danwood76 on 2009-08-27
Well can you return the partition to its original size?
If you can do that and then run fsck on the partition and it will fix it.

If you cant then there is a whole other mess of stuff we can try.

---

### Post by P4man on 2009-08-27
You're in trouble. Best bet is to first make an image of your partition with "dd". Then run testdisk and pray you can recover most of your files:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

(its in the universe or multiverse repo's, you can run it from a live cd ).

---

### Post by alimooghashang on 2009-08-27
thanks all
the problem was solved with checking disk in Gparted.
i Check the sda11 and all my files are currect
thanks all for help

---

### Post by Jose Catre-Vandis on 2009-08-31
> **ExtremeCoolSha said:**
> As Danwood76 stated Ext2FSD is a better one to mount Linux volumes in the Windows. But there is a restriction in this. Note these softs can't mount Logical Volumes. Do u have any configured partitions in Ubuntu as a Logical Volume, or simply primary partitions ?

This could well be true but has not been and is not my experience with W7 and XP using ext2fsd 0.48 with all my ext3 partitions in an extended partition in logical partitions

---

