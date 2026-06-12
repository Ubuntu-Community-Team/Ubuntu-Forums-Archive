---
title: "Adding a second hard drive ... How should I update fstab"
date: 2009-07-04
forum: General Help
---

### Post by sefs on 2009-07-04
Hi there, I added a second HD to my system.

My fstab currently looks like

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=c53e9d5a-14f5-4c64-8f72-4fc167d5551e /               ext3    relatime,errors=remount-ro 0       1
UUID=d8a6a7d3-6b4f-42b3-b72d-1db2b966900c /home           ext3    relatime        0       2
UUID=518ffaf9-8651-4347-95ad-42f3dd1e4a1d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

How should I adjust the above to ensure the drive is mounted and accessible to all users on the system.  The extra HD is in ext4

---

### Post by michy99 on 2009-07-04
Post the output of these commands.```
sudo fdisk -l
blkid
```

---

### Post by drs305 on 2009-07-04
Run this to get the UUID of the new drive:
```

sudo blkid -c /dev/null

```

For an ext4 partition: Make a mount point, I'll use /mnt/mynewdrive for the example, and make yourself the owner:
```

sudo mkdir /mnt/mynewdrive
sudo chown -R yourusername: /mnt/mynewdrive  # make yourself the owner

```

Edit fstab and add:
> 
UUID=90464cd4-d50c-46bd-8a3f-1a0c5a616a3f /mnt/mynewdrive ext4  defaults 0 2
or if you prefer
LABEL=VMWARE /mnt/mynewdrive ext4 defaults,users 02


Save fstab and remount:
```

sudo mount -a

```

[COLOR="Red"]EDITED[/COLOR] for information provided in post #4

---

### Post by sefs on 2009-07-04
> **michy99 said:**
> Post the output of these commands.```
sudo fdisk -l
blkid
```

```

$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d243

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826   83  Linux
/dev/sda2            2612       30401   223223175    5  Extended
/dev/sda5            2612       29878   219022146   83  Linux
/dev/sda6           29879       30401     4200966   82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74159f09

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4998    40146403+  83  Linux

```


```

$ blkid
/dev/sda1: LABEL="root" UUID="c53e9d5a-14f5-4c64-8f72-4fc167d5551e" TYPE="ext3" 
/dev/sda5: LABEL="data1" UUID="d8a6a7d3-6b4f-42b3-b72d-1db2b966900c" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="518ffaf9-8651-4347-95ad-42f3dd1e4a1d" 
/dev/sdb1: LABEL="VMWARE" UUID="90464cd4-d50c-46bd-8a3f-1a0c5a616a3f" TYPE="ext4" 
```

---

