---
title: "mount drive using termial......"
date: 2009-08-16
forum: General Help
---

### Post by abhilashm86 on 2009-08-16
its easy to umount in terminal than mount!!, i just plugged in a pen drive, here are status of my drives, how to mount using  terminal, 
if we right click, we have option mount volume, i want to do it in terminal

```
abhilash@abhilash:~$ sudo blkid
/dev/sda1: UUID="5AB85F79B85F529D" TYPE="ntfs" 
/dev/sda6: UUID="c098dd08-8b82-4dd6-b2b1-fff959ab7870" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="53b39459-d52d-4d6a-bdb2-1e6bfcabfb36" 
/dev/sda8: LABEL="SONGS" UUID="71B1-0D79" TYPE="vfat" 
/dev/sda9: LABEL="MUSIC" UUID="DCC5-0AE8" TYPE="vfat" 
/dev/sdb1: UUID="142B-29BD" TYPE="vfat" 

abhilash@abhilash:~$ mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```
how to do it??:)

---

### Post by rudy.b on 2009-08-16
You need to provide a mount point e.g. ```
sudo mount /dev/sdb1 /mnt/disk
``` where /mnt/disk already exists and /dev/sdb1 is the device you are mounting.

---

### Post by abhilashm86 on 2009-08-16
> **rudy.b said:**
> You need to provide a mount point e.g. ```
sudo mount /dev/sdb1 /mnt/disk
``` where /mnt/disk already exists and /dev/sdb1 is the device you are mounting.

when i tried, found this error,
```
abhilash@abhilash:~$ sudo mount /dev/sdb1 /mnt/disk
mount: mount point /mnt/disk does not exist

```
also i think there is no disk in /mnt, check this,
```

abhilash@abhilash:/mnt$ ls -a -l
total 8
drwxr-xr-x  2 root root 4096 2008-04-15 11:23 .
drwxr-xr-x 21 root root 4096 2009-06-24 07:46 ..

```
actually we should mount in /media/ right, because all hard drives and usb's automatically mount there........

---

### Post by mrbiggbrain on 2009-08-16
> **abhilashm86 said:**
> when i tried, found this error,
```
abhilash@abhilash:~$ sudo mount /dev/sdb1 /mnt/disk
mount: mount point /mnt/disk does not exist

```
also i think there is no disk in /mnt, check this,
```

abhilash@abhilash:/mnt$ ls -a -l
total 8
drwxr-xr-x  2 root root 4096 2008-04-15 11:23 .
drwxr-xr-x 21 root root 4096 2009-06-24 07:46 ..

```
actually we should mount in /media/ right, because all hard drives and usb's automatically mount there........

you can mount anywhere

and you need to do
```

sudo mkdir /mnt/disk
```

the directory isnt created yet

you could mount the disk as /hobo/lover/2009/woot/disk if you so chose, there is a standard protocol, but most people mount under /mnt/ and most programs seem to mount under /media/

---

### Post by abhilashm86 on 2009-08-16
> **mrbiggbrain said:**
> you can mount anywhere

and you need to do
```

sudo mkdir /mnt/disk
```

the directory isnt created yet

you could mount the disk as /hobo/lover/2009/woot/disk if you so chose, there is a standard protocol, but most people mount under /mnt/ and most programs seem to mount under /media/

yes thats what is confusing me, if there is a separate directory /mnt, why would most of drives, usb's will be mounted under /media?
so can i create a directory under /media as disk and mount other drives.......

i was able to mount under /mnt/disk, then under PLACES->COMPUTER, it was showing my two usb's which were mounted under /mnt/disk, but could not be opened there,
how to fix this or should i come to /mnt/disk, there i need to access the file?

---

### Post by mrbiggbrain on 2009-08-16
I belive this is meant to remove mistakes, by having most automated systems mount under /media/, and users mount under /mnt/, the programs arnt interfering with the user, what if a program tried to mount something as /mnt/disk and you had already mounted there.

and are you trying to mount 2 devices as the same mount point?

---

### Post by abhilashm86 on 2009-08-17
> **mrbiggbrain said:**
> 

and are you trying to mount 2 devices as the same mount point?

no actually i wanted to mount in /media/disk because like whenever other than me, who'll use my comp, they'll go to places->computer-> USB!! nothing opens and gone!!
some people don't know how exactly to use /mnt, now everything is clear......

i think we can't mount more than 1 device in same mount point??

---

