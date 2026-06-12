---
title: "need help recovering some files please"
date: 2011-10-05
forum: General Help
---

### Post by stacisharp on 2011-10-05
I had some trouble with my windows pc. it seems to be working now, but I have a 500gb C: drive and a 3tb R: drive that I use for data.  windows seems ok now, but the R: hard drive shows up in windows as uninitialized.  I think it was formatted ntfs.  I can see it if I go to disk utility in Ubuntu 11.04 as dev/sdb  but I can't mount it.. I don't really know anyting about linux or unix or terminal... I'm quite decent with windows, I built my own machine...

I have the data on the drive up to 9/29 at 11:19 am on a backup drive.  so all I really need is any data since then, and I can format and restore the rest.  Ideally,  I would like the drive to just work again but I realize that is unlikely.  

I googled a bit and tried typing this into terminal:
```
ubuntu@ubuntu:~$ sudo mount /dev/sdb /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mkdir /media/xyz
root@ubuntu:/home/ubuntu# mount -t fat32 /dev/sdb /media/xyz
mount: unknown filesystem type 'fat32'
root@ubuntu:/home/ubuntu# sudo mount -t ntfs-3g /dev/sdb /media/xyz
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@ubuntu:/home/ubuntu# 
```so I'm not sure what else, if anything I can do to make ubuntu mount the drive. any suggestions?

---

### Post by TeoBigusGeekus on 2011-10-05
> **stacisharp said:**
> ```

root@ubuntu:/home/ubuntu# sudo mount -t ntfs-3g /dev/sdb /media/xyz
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
[COLOR="Red"]Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR]
root@ubuntu:/home/ubuntu# 
```
Try with
```
sudo mount -t ntfs-3g /dev/sdb[COLOR="red"]1[/COLOR] /media/xyz
```

---

### Post by stacisharp on 2011-10-05
ok, tried that and here's what it said..... the disk may have been fat32 (i'm not certain) but I don't know the argument to try mounting as fat32.

```
 ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
        Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org
 
```so it seems vfat is the argument for fat32 so i did this:

```
root@ubuntu:/home/ubuntu# mount -t vfat /dev/sdb /media/xyz
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by TeoBigusGeekus on 2011-10-05
With the drive plugged in, can you post us the output of
```
sudo fdisk -l
```
?

---

### Post by stacisharp on 2011-10-05
absolutely.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x958c18ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT
ubuntu@ubuntu:~$ 
```

---

### Post by TeoBigusGeekus on 2011-10-05
Also the output of
```
sudo parted /dev/sdb print
```

---

### Post by Mark Phelps on 2011-10-05
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by stacisharp on 2011-10-05
```
ubuntu@ubuntu:~$ sudo parted /dev/sdb print
Error: /dev/sdb: unrecognised disk label                                  
ubuntu@ubuntu:~$ 

```

---

### Post by TeoBigusGeekus on 2011-10-05
If you try
```
sudo parted /dev/sdb1 print
```
?

---

### Post by stacisharp on 2011-10-05
```
ubuntu@ubuntu:~$ sudo parted /dev/sdb1 print
Error: Could not stat device /dev/sdb1 - No such file or directory.       
Retry/Cancel?     
```

---

### Post by TeoBigusGeekus on 2011-10-05
Are you sure the drive is plugged in?

---

### Post by stacisharp on 2011-10-05
yes. it's the sdb drive. fdisc saw it.  there are only 2 hard drives and 1 optical drive on this computer.  a 500gb hd and a 3tb hd.  it's in disk utility.  here's a screen shot.


_[IMG]http://img11.imageshack.us/img11/9403/screenshotore.png[/IMG]_[IMG]http://imageshack.us/photo/my-images/257/screenshotndn.png/[/IMG]

---

