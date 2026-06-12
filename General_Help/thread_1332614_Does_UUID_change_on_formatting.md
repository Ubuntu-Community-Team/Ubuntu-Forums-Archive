---
title: "Does UUID change on formatting?"
date: 2009-11-20
forum: General Help
---

### Post by emigrant on 2009-11-20
hi all,
i made a fstab entry for my pendrive using its uuid.
and later formatted it from fat32 to msdos. (to install portable linux).
and now i see the uuid has been chaged.

is it normal?

and in fstab, as fvat for fat32 what is for msdos?

thank you all.:popcorn:

---

### Post by blueridgedog on 2009-11-20
Yes...a format and a type change will change the ID.

---

### Post by bodhi.zazen on 2009-11-20
> **emigrant said:**
> hi all,
i made a fstab entry for my pendrive using its uuid.
and later formatted it from fat32 to msdos. (to install portable linux).
and now i see the uuid has been chaged.

is it normal?

and in fstab, as fvat for fat32 what is for msdos?

thank you all.:popcorn:

FAT is windows speak for vfat partitions

---

### Post by emigrant on 2009-11-20
> **bodhi.zazen said:**
> FAT is windows speak for vfat partitions
sorry for my bad english,
what i was asking is,
for a fat32 drive, you use vfat as the type in fstab.
like that, for a msdos type drive, what do you use in fstab?
i used msdos and it says its wrong.:o

---

### Post by bodhi.zazen on 2009-11-20
Should be msdos, you can try auto as well =)

What error did you get exactly ? Often reporting the exact error message is more helpful then simply stating that you are having a problem.

---

### Post by emigrant on 2009-11-20
thanks for your reply :popcorn:

i added this to fstab:
```
UUID=87ac1e22-c945-433d-9850-be9bf5efbd7a    /media/BigPen [COLOR=Red]msdos[/COLOR] users,auto,fmask=0111,dmask=0000   0   0
```

and got this error:
```

wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and the dmesg:


```

$ dmesg | tail
[ 6559.191900] FAT: bogus number of reserved sectors
[ 6559.191905] VFS: Can't find a valid FAT filesystem on dev sdb5.
[ 6593.261455] FAT: bogus number of reserved sectors
[ 6593.261459] VFS: Can't find a valid FAT filesystem on dev sdb5.
[ 6605.712900] FAT: bogus number of reserved sectors
[ 6605.712904] VFS: Can't find a valid FAT filesystem on dev sdb5.
[10342.457561] FAT: bogus number of reserved sectors
[10342.457564] VFS: Can't find a valid FAT filesystem on dev sdb5.
[10401.325127] FAT: bogus number of reserved sectors
[10401.325130] VFS: Can't find a valid FAT filesystem on dev sdb5.
```

and i added this:

```
UUID=87ac1e22-c945-433d-9850-be9bf5efbd7a    /media/BigPen [COLOR=Red]auto[/COLOR] users,auto,fmask=0111,dmask=0000   0   0
```

and got this error:

```
$ sudo mount -a
/dev/sdb5 looks like swapspace - not mounted
mount: you must specify the filesystem type

```

---

### Post by bodhi.zazen on 2009-11-20
Looks as if the partition is bad. Are you sure you have the correct partition ?

---

### Post by emigrant on 2009-11-20
i think i have not figured out something easy :(

fdisk:

```
Disk /dev/sdb: 4022 MB, 4022337536 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83f5fd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         460     3694918+   b  W95 FAT32
/dev/sdb2             461         489      232942+   5  Extended
/dev/sdb5             461         489      232911   82  Linux swap / Solaris

```

through fdisk it shows the disk is fat32, 
but when i right click it shows msdos :(

---

### Post by emigrant on 2009-11-20
by the way i see you today cruising through the support sections :D

---

### Post by bodhi.zazen on 2009-11-20
Did you format the partition to msdos ?

---

### Post by sisco311 on 2009-11-20
msdos in not a filesystem type, it's a partition table type. 

to get the filesystem type of the partitions:
```
sudo blkid
```

---

### Post by emigrant on 2009-11-20
no. i formated it to fat32 and installed puppylinux through 'live usb creater'.
and for vfat also i get the same message:
```

wrong fs type, bad option, bad superblock on /dev/sdb5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

---

### Post by emigrant on 2009-11-20
> **sisco311 said:**
> msdos in not a filesystem type, it's a partition table type. 

to get the filesystem type of the partitions:
```
sudo blkid
```

thanks,
output:
```

$ sudo blkid
/dev/sda1: UUID="ECBC27FCBC27C046" TYPE="ntfs" 
/dev/sda2: UUID="8CF2728BF27278F2" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="bd49a241-1650-4369-82ae-726b389bc10c" 
/dev/sda5: UUID="becef1b2-d864-4764-828f-6381e90fd95d" TYPE="ext4" 
/dev/sda6: TYPE="swap" UUID="2c7425b6-d64e-d288-ae82-bf2580cd63c4" 
/dev/sda7: TYPE="swap" UUID="ed9e5e83-f61c-4f72-b6d8-0bdda6c0e3b7" 
/dev/sdb1: UUID="0A77-AF04" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="87ac1e22-c945-433d-9850-be9bf5efbd7a" 
```

---

### Post by bodhi.zazen on 2009-11-20
> **sisco311 said:**
> msdos in not a filesystem type, it's a partition table type. 

to get the filesystem type of the partitions:
```
sudo blkid
```

I believe there is a msdos file system, although I have not used it (not an expert on msdos).

[http://linux.about.com/library/cmd/blcmdl8_mkfs.msdos.htm](http://linux.about.com/library/cmd/blcmdl8_mkfs.msdos.htm)

---

### Post by sisco311 on 2009-11-20
> **emigrant said:**
> thanks,
output:
```

$ sudo blkid
/dev/sda1: UUID="ECBC27FCBC27C046" TYPE="ntfs" 
/dev/sda2: UUID="8CF2728BF27278F2" TYPE="ntfs" 
/dev/sda3: TYPE="swap" UUID="bd49a241-1650-4369-82ae-726b389bc10c" 
/dev/sda5: UUID="becef1b2-d864-4764-828f-6381e90fd95d" TYPE="ext4" 
/dev/sda6: TYPE="swap" UUID="2c7425b6-d64e-d288-ae82-bf2580cd63c4" 
/dev/sda7: TYPE="swap" UUID="ed9e5e83-f61c-4f72-b6d8-0bdda6c0e3b7" 
/dev/sdb1: UUID="0A77-AF04" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="87ac1e22-c945-433d-9850-be9bf5efbd7a" 
```

/dev/sdb1 is a vfat partition, which is okay since you have to format the USB drive's partition to fat16 in order to install Ubuntu on it.

In Jaunty and Karmic you can use USB Startup Disk Creator (System -> Administration).

How did you install Ubuntu/Linux on the drive?

[http://www.pendrivelinux.com]("http://www.pendrivelinux.com")

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by emigrant on 2009-11-20
i went to windows, (since the [downloaded application]("http://www.pendrivelinux.com/linux-live-usb-creator/") is .exe), formatted the drive to fat 32, and installed pupply linux.

---

### Post by sisco311 on 2009-11-20
> **emigrant said:**
> i went to windows, (since the [downloaded application]("http://www.pendrivelinux.com/linux-live-usb-creator/") is .exe), formatted the drive to fat 32, and installed pupply linux.

In your fstab entry change the UUID to *0A77-AF04* (the uuid of /dev/sdb1 the fat partition) and the type to *vfat*.

---

### Post by emigrant on 2009-11-20
thank you very much, it worked :)

---

