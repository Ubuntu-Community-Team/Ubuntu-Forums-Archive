---
title: "Hard disk Access"
date: 2011-02-28
forum: General Help
---

### Post by MagnaFX on 2011-02-28
New to linux, Halp!

I am running with 3 hard disks on my computer. One is a 750 gb drive that Win7 is installed on. A 500 with Ubuntu installed and partitioned. And the last one is a 500 that i use as a storage drive for movies, downloads and such. 

When booted in ubuntu, I can access the 750 drive with windows installed but not the 500 gb Data drive. I have tried going into prefrences and mounting the drive manually but it keeps coming up with /dev/sdb1 is already mounted, yet i cannot access it in /media or in places in gnome. 

However, when loaded in win7, i cannot access the 500 with ubuntu on it but i can access the drive with the data on it.

Please advise!

---

### Post by seawolf167 on 2011-02-28
Windows doesn't like to play nice with other formats (i.e. ext3) so Windows won't be able to read your Ubuntu file system.

In Ubuntu, can you run the following commands so we can see what is mounted and what partitions exist

```
mount
```

and

```
sudo fdisk -l
```

---

### Post by grahammechanical on 2011-02-28
If I understand the Linux naming codes correctly then, sda would be the first drive (the Windows one), sdb would be the second drive (the Ubuntu one). This means that the third drive should be sdc. You are looking at sdb1, which (if I am correct and I can be wrong, often) is the first partition on the second drive. There should be a second partition on the second drive, which would be sdb2.

The Disc Utility should help get a better picture of what is in your machine. Literally.

Again if I am correct, then I would say that you can indeed access sdb1 in Places. Click on Home Folder and you will see this drive/partition listed as File System.

The drive or partition where Ubuntu is installed is listed as File System and not as a drive. If you have set up the Home folder on a drive or partition it will simply be listed as Home Folder. The user does not need to be aware that he is accessing drives or partitions. This is great for those who just want to use the machine. It is only drives/partitions other than these two that are shown with a disc drive icon.

Regards.

---

### Post by MagnaFX on 2011-02-28
Mount

```
/dev/sdc1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/magnum/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=magnum)
/dev/sda1 on /media/7E58E8ED58E8A4DD type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

fdisk -l

```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032140

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c5647b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036501

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58336   468581376   83  Linux
/dev/sdc2           58336       60802    19802113    5  Extended
/dev/sdc5           58336       60802    19802112   82  Linux swap / Solaris

```

---

### Post by MagnaFX on 2011-02-28
When i use the disk utility and hit mount volume, it gives me this error

```


Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed


```

---

### Post by seawolf167 on 2011-02-28
> **MagnaFX said:**
> 
```
/dev/sdc1 on / type ext4 (rw,errors=remount-ro,commit=0)
/dev/sda1 on /media/7E58E8ED58E8A4DD type fuseblk 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58336   468581376   83  Linux
/dev/sdc2           58336       60802    19802113    5  Extended
/dev/sdc5           58336       60802    19802112   82  Linux swap / Solaris
[/code]

/dev/sdc* are your linux partitions, you won't be able to mount them because they are already mounted (i.e. in use since your computer is turned on and booted into Ubuntu

/dev/sda1 is mounted and should be accessible via the Places menu

You have a couple options to mount /dev/sdb1

Graphically:

System -> Administration -> Disk Utility -> Click to select the drive 

i.e.

```
Disk /dev/sdb: 500.1 GB
```

You'll know its the correct one because it will give you the option to "Mount Volume" in the lower-middle of the window, click that, then you can access it from the Places menu

Command Line:

Open a terminal and type

```
sudo mkdir /media/datamount
sudo mount /dev/sdb1 /media/datamount
```

Now this will be accessible from the Places menu (if not, simply browse to /media/datamount

---

### Post by MagnaFX on 2011-02-28
Yea, it would be that easy. Any explanation on what happenned and why it had to be done manually? Thank you very much for your help btw.

---

### Post by seawolf167 on 2011-02-28
Ubuntu only auto mounts the entries that are specified in a config file located at /etc/fstab. You can see what this file looks like by typing in the following command in a terminal:

```
gedit /etc/fstab
```In order to automatically mount this volume, you will have to add a line in this config file. For your system the line you want to add is (where *somemountpoint* is what you want to call your mounted drive):

```
sudo mkdir /media/somemountpoint
sudo umount /dev/sdb1
gksudo gedit /etc/fstab
```add this line at the end of the file, then save & exit

```
#Entry for /dev/sdb1 :
/dev/sdb1    /media/somemountpoint    ntfs-3g    defaults,locale=en_US.utf8    0    0
```

---

### Post by MagnaFX on 2011-02-28
Do i delete the entry 

```
/dev/sdb1       /               ext4    errors=remount-ro 0       1
```

---

### Post by seawolf167 on 2011-02-28
> **MagnaFX said:**
> Do i delete the entry 
```
/dev/sdb1       /               ext4    errors=remount-ro 0       1
```

Yes, because for whatever reason, that has the wrong format type and mount point

From your earlier post, this is /dev/sdb1:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS
```and you can see that its type is NTFS, not ext4, and it is trying to mount at /, but your / filesystem is:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58336   468581376   83  Linux
/dev/sdc2           58336       60802    19802113    5  Extended
/dev/sdc5           58336       60802    19802112   82  Linux swap / Solaris
```

And is mounted as such:


```
/dev/sdc1 on / type ext4 (rw,errors=remount-ro,commit=0)
```

Just in case, you should make a backup of /etc/fstab before you delete it:

```
sudo cp /etc/fstab /etc/fstab.backup
```

---

