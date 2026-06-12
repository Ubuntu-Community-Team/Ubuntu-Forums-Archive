---
title: "Mounting a raid 0 ntfs in ubuntu"
date: 2006-02-07
forum: General Help
---

### Post by mecea04 on 2006-02-07
Hey, here is my problem/question:

I have Ubuntu 5.10 installed on a 20gig WD HD, and 320gig WD setup with Raid0 where my windows setup is, NTFS format.  Im just wondering if it is possible to mount the raid0 setup while inside ubuntu so I can read the data off it?  If so how would I go about it?  Thanks!

---

### Post by Horndog on 2006-02-07
Start by looking [here.]("http://ubuntuguide.org/#mountunmountntfs")

---

### Post by mecea04 on 2006-02-08
well I tried that, but I tried again.  Here is what it tells me.

root@Mecea04:~# sudo fdisk -l

Disk /dev/hda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2389    19189611   83  Linux
/dev/hda2            2390        2495      851445    5  Extended
/dev/hda5            2390        2495      851413+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321    c  W95 FAT32 (LBA)
root@Mecea04:~# sudo mount /dev/sda /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@Mecea04:~# dmesg | tail
[4294820.900000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294820.900000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[4294821.450000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294821.450000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294821.450000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[4294899.184000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4295072.839000] printk: 6 messages suppressed.
[4295072.839000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4295072.839000] NTFS-fs error (device sda): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4295072.839000] NTFS-fs error (device sda): ntfs_fill_super(): Not an NTFS volume.

---

### Post by mecea04 on 2006-02-08
I also mounted sda, and sdb with no luck.

---

### Post by lamego on 2006-02-08
You can't mount sda or sdb because they are disks not partitions.
You must mount sda1 ...

---

### Post by mecea04 on 2006-02-08
Okay, I mounted the sda1 and this is what happens.  I also deleted the space from sda1 /media..., I got the same error as above with the space there.

root@Mecea04:~# mount /dev/sda1/media/windows/ -t ntfs -o nls=utf8,umask=0222
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by n5jyk on 2006-02-09
check /dev/mapper to see if it mounted the raid already. don't fuss about the strange name it may have given it. if you have more than one partition or slice on the raid it will be like "isw_dciegdfjj_RAID_Volume11"  and so on.

If it didn't already do it for you. install dmraid (search for it in synaptic) and reboot (just because its easier) then take a look at /dev/mapper.

then you can put something like this in your /etc/fstab
/dev/mapper/isw_dciegdfjj_RAID_Volume11   /media/raid0   ntfs  (options here)

EDIT: Don't forget that you need a real mount point for the filesystem. You could use /mnt or /media/raid0. but if you choose a mount point that doesn't exist like /media/raid0, you would have to mkdir /media/raid0 before you mount there.

all other fstab and mounting rules apply of course. (in other words - any farther and we get over my head for ubuntu)

-b

---

### Post by dcstar on 2006-02-09
[QUOTE=mecea04]Hey, here is my problem/question:

I have Ubuntu 5.10 installed on a 20gig WD HD, and 320gig WD setup with Raid0 where my windows setup is, NTFS format.  Im just wondering if it is possible to mount the raid0 setup while inside ubuntu so I can read the data off it?  If so how would I go about it?  Thanks![/QUOTE]
If the Windows RAID is done by software, I would not even contemplate touching it with another OS.

If it is done by hardware, it **might** be accessible if you have exactly the right drivers for it **and** it specifically says that Linux can access the array - otherwise you are playing with proverbial "fire"!!!!!              [-X

---

### Post by mecea04 on 2006-02-09
Thanks for the information, it was exactly what I needed to get it to work.  much appreciated!! \\:D/

---

### Post by Breepee on 2006-04-02
Hope you don't mind I revive this thread once more, but I've got a question about mounting Windows RAID0 volumes too.

I'm planning the following setup (with two 200GB drives):

drive 1: 100GB Windows, 100GB RAID0 (one half)
drive 2: 100GB Ubuntu,   100GB RAID0 (the other half)

Those two pieces of 100GB will be used to create a RAID0 volume in Windows, totaling into an array of 200GB. My question is: can this be done?

I by the way wouldn't mind doing it the other way round: creating a Linux RAID0 volume, but mounting that in Windows just is not possible at all I think...

---

### Post by Breepee on 2006-04-02
Does anyone know this?

---

### Post by Horndog on 2006-04-02
[QUOTE=Breepee]
 	Does anyone know this?[/QUOTE]

You will get a better response if you start a new thread. I personally will not help anyone who hijacks a thread and I'm sure others feel the same way.

---

### Post by Breepee on 2006-04-02
As you could see, the problem of the other person was solved, so there's no hijacking involved. On some other forums I visit it's customary to re-use threads in this manner.

---

### Post by Horndog on 2006-04-02
Well good luck then ;)

---

### Post by Breepee on 2006-04-02
You don't *have* to post you know...

Created a new thread so that everyone's happy :)

---

### Post by Horndog on 2006-04-02
[QUOTE=Breepee]You don't *have* to post you know...

Created a new thread so that everyone's happy :)[/QUOTE]

What the hell is wrong with you? Your the one that needs help not me! I don't know anyone that would help you with that attitude.

---

### Post by Breepee on 2006-04-02
It seems to me you're only going offtopic and worrying about not giving hypothetical help. You told me it's smarter to create a new thread and I did.

For the record: the new thread is here: [http://ubuntuforums.org/showthread.php?p=885170](http://ubuntuforums.org/showthread.php?p=885170)

---

### Post by Horndog on 2006-04-02
I think It's time to close this thread.

---

