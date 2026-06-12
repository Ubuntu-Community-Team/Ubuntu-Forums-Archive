---
title: "how to hide network &amp; floppy drive in nautilus?"
date: 2009-07-23
forum: General Help
---

### Post by bionnaki on 2009-07-23
hello.

how would I hide or remove the floppy drive and network places within nautilus? I do not have a floppy drive nor a home network.

thanks.

---

### Post by bionnaki on 2009-07-26
anyone?

---

### Post by regstraton on 2009-11-05
A question I have had on my mind for some time now.

The solution turns out to be easy:

[COLOR="Blue"]-> Specifically map the drive to mount in /mnt rather then /media.
[/COLOR]

_**Further**_
There are various situations where I haven't wanted to see drives shown in Nautilus. eg: I have a multi-boot computer and don't wish to see the partitions of other OSes. I have a USB disk with several partitions, yet I only wish to see my data partition when I plug it in. I use a USB Mobile Broadband adapter and it has drive with windows install files on it.

_**How To**_
Discover the UUID of the partition/drive you wish to hide. If it is not mounted, then use Nautilus to mount it. Then in a terminal run
```
$ mount
/dev/sdc1 on /media/MyUSB_BOOT type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdc2 on /media/MyUSB_DATA type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush
```
Find your partition/drive and get the device path, eg: /dev/sdc1. Now using the device path use:
```
$ sudo vol_id /dev/sdc1
[sudo] password for user: 
ID_FS_USAGE=filesystem
ID_FS_TYPE=vfat
ID_FS_VERSION=FAT16
ID_FS_UUID=496E-490E
ID_FS_LABEL=MyUSB_BOOT
ID_FS_LABEL_ENC=MyUSB_BOOT
```

Edit the /etc/fstab (taking care not to change anythng else):
```
$ sudo gedit /etc/fstab &
```

From the output of 'vol_id' construct the following line and add it as a new-line to /etc/fstab (note the spaces must actually be a single TAB character):
```
UUID=496E-490E  /mnt/MyUSB_BOOT  vfat
```

Add a corresponding directory to /mnt so that you can mount it if you wish to:
```
$ sudo mkdir /mnt/MyUSB_BOOT
```

And if you ever wish to mount this drive/partition, this will do it for you:
```
$ sudo mount /mnt/MyUSB_BOOT
```
And to un-mount:
```
$ sudo umount /mnt/MyUSB_BOOT
```

I suggest using the UUID rather than using the device path because the device path gets reused for removable devices, where the UUID specifically references a a single removable device.

---

