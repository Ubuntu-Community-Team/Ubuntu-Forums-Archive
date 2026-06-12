---
title: "trying to mount my flash drive to install an OS to boot to"
date: 2012-02-03
forum: General Help
---

### Post by imachavel on 2012-02-03
sudo fdisk -l
[sudo] password for danel: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ded99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    95379456   658579455   281600000   83  Linux
/dev/sda2       658581502   976771071   159094785    5  Extended
/dev/sda5       853129216   924809215    35840000   82  Linux swap / Solaris
/dev/sda6       658581504   776222719    58820608   83  Linux
/dev/sda7       776224768   781449215     2612224   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001342b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    31266815    15633392   83  Linux


I'm using this guide:

[http://www.novell.com/coolsolutions/feature/11637.html](http://www.novell.com/coolsolutions/feature/11637.html)

is my flash drive on /dev/sdb1? Sorry, it has to be, it says 16.0 gb, 16008609792 bytes. I wonder what dev/sdc1 is? Oh well

Ok let's hope this works

---

### Post by collisionystm on 2012-02-03
Im guessing /dev/sdc is it

type

df -kh

post output

---

### Post by imachavel on 2012-02-03
yes I've had a bit of a fail:

#pwd
/home/danel
#danel@danel-Dimension-4700:~$ mount -t vfat -o uid=danel, gid=users /dev/sdc /home
mount: only root can do that
#danel@danel-Dimension-4700:~$ sudo mount -t vfat -o uid=danel, gid=users /dev/sdc /home
[sudo] password for danel: 
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
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .



ok here is what you wanted:

#df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             265G  106G  146G  43% /
udev                  1.5G  4.0K  1.5G   1% /dev
tmpfs                 605M  1.2M  604M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  1.5G  316K  1.5G   1% /run/shm
/dev/sdb1             233G   97G  137G  42% /media/WD Passport
/dev/sda6              56G  7.2G   46G  14% /media/8bd7df9e-99fb-40b8-99ae-5a155f67b421
/dev/sdc1              15G   38M   14G   1% /media/230b7ffe-bb7a-4723-ba30-b8b58f7fc8d8

---

