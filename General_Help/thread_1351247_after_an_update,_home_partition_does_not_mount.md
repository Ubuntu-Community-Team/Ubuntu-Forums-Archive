---
title: "after an update, home partition does not mount"
date: 2009-12-10
forum: General Help
---

### Post by kkllss on 2009-12-10
After a small update in karmic, my home partition (/dev/sda6) no longer mounts.  Both normal boot and recovery mode drop to a recovery console after mounting /home fails. I have booted up a live usb karmic to investigate.  I can mount all my other partitions on the harddisk.  In Gparted my home partition is now missing the mount point but everything else appears normal. In Palimpsest Disk Utility my home partition shows up as Unrecognized - Unknown or Unused.  Fdisk shows the partition and info correctly. I have also looked at my fstab and it appears to be normal but I do not have much experience reading it.

I really do not mind reinstalling if necessary but _I would like to mount my home partition and back up my files_ first.

---

### Post by lmarmisa on 2009-12-10
Maybe it's a problem with the UUID of the home partition.

Is the root user account activated?. If so, that would be fine because this users does not need the /home partition (the home directory for the superuser is /root).

Could you post the results of these commands?

```

sudo bash # Not needed if root

fdisk -l

blkid

cat /etc/fstab


```Best regards,

Luis

---

### Post by kkllss on 2009-12-10
hello, thank you for your reply. here are the outputs of the commands you requested.

fdisk
> ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f8b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78140128+   5  Extended
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        9729       12339    20972857+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           12340       19457    57175335    b  W95 FAT32
/dev/sda5               1        1245    10000368   83  Linux
/dev/sda6            1246        9230    64139481   83  Linux
/dev/sda7            9231        9728     4000153+  82  Linux swap / Solaris

I am not sure how to properly invoke blkid. Do I use the sda6 UUID? 

cat /etc/fstab
> ubuntu@ubuntu:~$ cat /media/root/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b8b71336-b07b-4829-a18b-fa2f3bcadc3e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=51899da1-5cfd-4b0c-ad4b-8d2e87792a03 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=be792331-be26-414c-a919-9b7db8a6ccd4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by lmarmisa on 2009-12-10
Only type:

```

sudo blkid         #use sudo only if you are not superuser

```

blkid command does not require any parameter.

Are you using a very old version of Ubuntu?.

Regards,

Luis

---

### Post by hawthornso23 on 2009-12-10
sudo blkid -s UUID


... will list the UUID's of all your disks. Then you can check whether those UUIDs match the ones in fstab.

---

### Post by hawthornso23 on 2009-12-10
[B]OOPS - sorry about the multipost. Had a rejection of IP address. The forums are acting up a bit today.
[/B] 

sudo blkid -s UUID

... will list the UUID's of all your disks. Then you can check whether those UUIDs match the ones in fstab.

---

### Post by kkllss on 2009-12-10
thanks everyone.

I am using karmic

here is the output of blkid

> blkid -s UUID
/dev/loop1: UUID="aaeb8212-6378-41ba-aaf1-4a7eb080748f" 
/dev/sda2: UUID="6CB8AD02B8ACCC40" 
/dev/sda3: UUID="D4B4-395C" 
/dev/sda5: UUID="b8b71336-b07b-4829-a18b-fa2f3bcadc3e" 
/dev/sda7: UUID="be792331-be26-414c-a919-9b7db8a6ccd4" 
/dev/sdb1: UUID="1794-2AA9" 

my home partition was /dev/sda6.

---

### Post by lmarmisa on 2009-12-10
The UUID of your home partition is missing. This is the problem.

Try this command:

```

sudo tune2fs -U "51899da1-5cfd-4b0c-ad4b-8d2e87792a03" /dev/sda6

```

and then repeat the blkid command.

Regards,

Luis

---

### Post by kkllss on 2009-12-10
thank you I really appreciate the support from everyone.
 
unfortunately that command did not change the output of blkid.

> ubuntu@ubuntu:~$ sudo tune2fs -U "51899da1-5cfd-4b0c-ad4b-8d2e87792a03" /dev/sda6
tune2fs 1.41.9 (22-Aug-2009)

ubuntu@ubuntu:~$ sudo blkid -s UUID
/dev/loop1: UUID="aaeb8212-6378-41ba-aaf1-4a7eb080748f" 
/dev/sda2: UUID="6CB8AD02B8ACCC40" 
/dev/sda3: UUID="D4B4-395C" 
/dev/sda5: UUID="b8b71336-b07b-4829-a18b-fa2f3bcadc3e" 
/dev/sda7: UUID="be792331-be26-414c-a919-9b7db8a6ccd4" 
/dev/sdb1: UUID="1794-2AA9" 

Is it important to note that I am working from a live usb trying to fix the installed system?

---

### Post by lmarmisa on 2009-12-10
The home partition seems damaged.


Are you able to mount the partition manually?. Working from the Gnome menu: Places -> Partition Size or Partition Name (sorry I don't know how the system labels it).

Live CD is no problem.

Regards,

Luis

---

### Post by kkllss on 2009-12-10
the home partition does not show up under the places.  It is the only partition I can not find, I have all the other partitions mounted.

really my only concern is the data (schoolwork, music, and pictures)
I am totally fine with reinstalling karmic (I would actually like to delete my Windows partition and increase my storage partition anyway)

The irony of this is that my girlfriend uses ubuntu as well, and for her setup I made a /root, /home, swap, and a dedicated /storage where she saves data. If only I had done the same haha.

---

### Post by lmarmisa on 2009-12-10
Hmmm.

Try to mount your partition in this way:

```

sudo mount /dev/sda6 /mnt 

```and check if the mount command was successful

```

mount 

```Regards,

Luis

---

### Post by kkllss on 2009-12-10
thank you.

those commands produced alot of output, but alas, /dev/sda6 did not mount

> ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda5 on /media/root type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda3 on /media/STORAGE type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda2 on /media/6CB8AD02B8ACCC40 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


---

### Post by lmarmisa on 2009-12-10
The fsck command will try to repair your partition:

```

sudo fsck -V /dev/sda6

```

---

### Post by hawthornso23 on 2009-12-10
Try

blkid -p sda

(according to man the -p option probes the device and doesn't just read the cache)

Guessing here, but sounds like it might help.
[B]
[then run blkid again afterwards to display results]][/B]

---

### Post by kkllss on 2009-12-10
thanks everyone.

fsck -V  

> ubuntu@ubuntu:~$ sudo fsck -V /dev/sda6
fsck from util-linux-ng 2.16
[/sbin/fsck.ext2 (1) -- /dev/sda6] fsck.ext2 /dev/sda6 
e2fsck 1.41.9 (22-Aug-2009)
home: clean, 11377/4014080 files, 961769/16034870 blocks


> blkid -p sda
does not do anything, is the syntax correct?

also I tried checking the partition in Gparted (redundant?)
> 
Check and repair file system (ext4) on /dev/sda6  00:00:05    ( SUCCESS )
     	
calibrate /dev/sda6  00:00:00    ( SUCCESS )
     	
path: /dev/sda6
start: 20000988
end: 148279949
size: 128278962 (61.17 GiB)
check file system on /dev/sda6 for errors and (if possible) fix them  00:00:05    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda6
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

11377 inodes used (0.28%)
148 non-contiguous files (1.3%)
13 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 7668/25/2
961769 blocks used (6.00%)
0 bad blocks
1 large file

6365 regular files
1331 directories
0 character device files
0 block device files
0 fifos
0 links
3671 symbolic links (3671 fast symbolic links)
1 socket
--------
11368 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
resize2fs /dev/sda6
     	
resize2fs 1.41.9 (22-Aug-2009)
The filesystem is already 16034870 blocks long. Nothing to do!

---

### Post by lmarmisa on 2009-12-10
It looks great!.

These two lines seem promising :D:

```

6365 regular files
1331 directories

```Try now

```

sudo fsck -vf /dev/sda6
sudo mount -t ext4 /dev/sda6 /mnt
mount

```

---

### Post by kkllss on 2009-12-10
thanks everyone for your time and effort

```
sudo fsck -vf /dev/sda6
sudo mount -t ext4 /dev/sda6 /mnt
mount
```

worked

the home partition has been mounted, and I am able to backup my files.
I am going to reinstall karmic later and create a large separate /storage partition to avoid problems again later. (plus I have some Windows 7 RC to delete as well).

I am particularly excited to be able to keep all my programming class assignments(some were on the cloud but not all).

so again thank you so much for your help

---

### Post by lmarmisa on 2009-12-10
First of all, congratulations.

I think that it is not necessary to reinstall karmic. If you are able to mount the /dev/sda6 partition manually, the automation of this process using /etc/fstab will be trivial.

No problem if you want to move your data to other storage partition later. But I would recommend you to fix your system now. Of course, the backup is a very good decision.

Best regards,

Luis

---

