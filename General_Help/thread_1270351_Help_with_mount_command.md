---
title: "Help with mount command"
date: 2009-09-19
forum: General Help
---

### Post by edpatterson on 2009-09-19
I recently discovered the System Rescue CD and it's ability to make a bootable thumb drive that saves changes (mount points, Firefox extensions, etc). It uses something called backstore to perform this magic. I managed to fill my backstore file. The site has directions on how to 'grow' the backstore file. It requires that you boot from the device, mount the device and issue a command.

When I try to mount the device I get a device busy error. When I tried the remount option I received a 'you need to specify the filesystem' error. Reading the man pages did not help me figure out just where to insert the WIN95 or FAT32 filesystem.

Here is the meat of my post on the support site:

```

boot: rescuecd backstore=off

sfdisk -l showed me the thumbdrive is at /dev/sdb1 and is of type WIN95 FAT32 (LBA)
Next I tried

mkdir /mnt/backstore
mount -o remount,rw /dev/sdb1 /mnt/backstore

That threw the error

mount: you must specify the filesystem type

```
I realize this is not the Rescue CD support site. It is that I know there are a lot of very experienced users here that probably know the answer off the top of their heads.

Thanks for any and all help.

Ed

---

### Post by falconindy on 2009-09-19
mount fat32 -o <options> <mount point>

---

### Post by Bachstelze on 2009-09-19
If your drive is already mounted, can't you just use that instead of remounting it?

---

### Post by Bachstelze on 2009-09-19
> **falconindy said:**
> mount fat32 -o <options> <mount point>

Wrong. It's [font=monospace]mount -t vfat -o options <device> <mount point>[/font].

---

### Post by edpatterson on 2009-09-19
I tried
```

mount fat32 -o rw,remount /dev/dsb1 /mnt/backstore

```
It showed me the help screens for mount. Then I issued the mount commandt to see just where and how the thumb drive was mounted
```

/dev/sdb1 on /mnt/cdrom type vfat (ro,fmask=0133,dmans=0022,codepage=cp437,iocharset=ascii)

```
I assume the rw,remount command will allow one device to be mounted more than once with difference permissions.

There is a file in the root of the thumbdrive, sysrcd.bs that I have to write to.

---

### Post by Bachstelze on 2009-09-19
> **edpatterson said:**
> 
I assume the rw,remount command will allow one device to be mounted more than once with difference permissions.


It won't. A device cannot be mounted more than once. But if it's currently mounted read-only and you want it mounted read-write, that's the way to go indeed.

---

