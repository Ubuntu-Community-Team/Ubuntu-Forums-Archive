---
title: "Mount by volume label?"
date: 2010-06-03
forum: General Help
---

### Post by directedition on 2010-06-03
I have a bootable USB stick of Ubuntu, and also on that stick is a small FAT32 partition where I can share files with windows. I need to be able to use this on any machine (so it won't always be sdb, sdc, or any predictable /dev designation like that) and I need it to mount on boot. Is there any way to create an entry in fstab that mounts a partition based on its volume label?

---

### Post by aeiah on 2010-06-03
not on volume label, but on uuid.
in your fstab you'll probably notice something like this:
```

# /home was on /dev/sdc5 during installation
UUID=28e1416d-509a-42ce-891a-e877b6b63823 /home           ext4    defaults        0       2

```

obviously this is for my ext4 home partition so things will be different for FAT, but the first two bits will be similar for you. 

with the drive plugged in, open a terminal and find out it's uuid. issue:
```

ls -l /dev/disk/by-uuid

```
this will give you your uuids for all your partitions, and you can use this in your fstab in place of '/dev/sdb1' or whatever.

---

### Post by Morbius1 on 2010-06-03
Yes you can.

Run the following command so you can get the correct label designation:
```
sudo blkid -c /dev/null
```Make a permanent home for that partition to live in. For example:
```
mkdir /home/morbius/CORSAIR
```Then add a line to /etc/fstab that will mount the partition by label when you insert the drive into the USB port:

For Example:
```
LABEL=CORSAIR /home/morbius/CORSAIR vfat user,umask=007,utf8,flush,noauto 0 0
```Or if you can guarantee that the USB drive is on before you boot you can instead set the fstab like this:

```
LABEL=CORSAIR  /home/morbius/CORSAIR vfat  utf8,umask=007,gid=46 0       0
```

---

### Post by directedition on 2010-06-03
If I clone the stick, will the UUID stay the same?

---

### Post by dcstar on 2010-06-03
> **directedition said:**
> I have a bootable USB stick of Ubuntu, and also on that stick is a small FAT32 partition where I can share files with windows. I need to be able to use this on any machine (so it won't always be sdb, sdc, or any predictable /dev designation like that) and I need it to mount on boot. Is there any way to create an entry in fstab that mounts a partition based on its volume label?

There is no need whatsoever to do anything with fstab because Ubuntu will use any partition label that exists for a mount point by default.

Put a label on any partition on your USB drive and it will be mounted by that name in /media when inserted.

If you want to access it from elsewhere then make a link to that name.

---

### Post by Morbius1 on 2010-06-03
> **dcstar said:**
> There is no need whatsoever to do anything with fstab because Ubuntu will use any partition label that exists for a mount point by default.
You know, I've gotten so used to answering this question for those folks where the automounting of usb drives doesn't work or it does work but it mounts read-only that I just assumed this was the underlying issue here.

My mistake :oops:

---

### Post by directedition on 2010-06-03
> **dcstar said:**
> There is no need whatsoever to do anything with fstab because Ubuntu will use any partition label that exists for a mount point by default.

Well, I was kinda hoping to be able to mount it to /home, so everything but the user's folder is immutable.

---

### Post by bodhi.zazen on 2010-06-03
> **directedition said:**
> Well, I was kinda hoping to be able to mount it to /home, so everything but the user's folder is immutable.

You can not use FAT or NTFS as a /home partition.

If you want an immutable /home I suggest you look as kiosk options.

    [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

google kiosk and you will find additional tutorials.

---

