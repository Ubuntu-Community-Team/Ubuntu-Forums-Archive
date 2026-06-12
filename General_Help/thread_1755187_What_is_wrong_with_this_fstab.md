---
title: "What is wrong with this fstab?"
date: 2011-05-10
forum: General Help
---

### Post by josephellengar on 2011-05-10
Hi. I have multiple drives that I use on a regular basis in my fstab. I have a secondary hard drive in my laptop that automatically mounts to ~/storage (formatted ntfs), a flash drive that automatically mounts to ~/flash (formatted vfat), and an external hard drive that does not automatically mount but I am trying to get it to automatically mount to ~/external. Right now it is trying to automatically mount to ~/flash, since both drives are /etc/sdc1, which is problematic because they are different filesystems. Do you have any idea how I might fix this problem? This is what my fstab looks like:

```


# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

#home
/dev/sda6 /home ext4 errors=remount-ro,discard 0 1

#storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user,noauto,exec 0 0

#external hard drive- this doesn't mount drive for some reason
/dev/sdc1 /home/ross/external ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#tmpfs
tmpfs /tmp tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0
tmpfs /usr/src tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives tmpfs defaults,noatime 0 0
tmpfs /var/log tmpfs defaults,noatime 0 0

```

---

### Post by blind2314 on 2011-05-10
> **josephellengar said:**
> Hi. I have multiple drives that I use on a regular basis in my fstab. I have a secondary hard drive in my laptop that automatically mounts to ~/storage (formatted ntfs), a flash drive that automatically mounts to ~/flash (formatted vfat), and an external hard drive that does not automatically mount but I am trying to get it to automatically mount to ~/external. Right now it is trying to automatically mount to ~/flash, since both drives are /etc/sdc1, which is problematic because they are different filesystems. Do you have any idea how I might fix this problem? This is what my fstab looks like:

```


# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0

# root filesystem
UUID=098c0e33-2ea8-420a-a7c9-2bcdc9011118 / ext4 errors=remount-ro,discard 0 1

# swap file
UUID=0de4ba0c-7406-4974-a25b-a1d10f68be39 none swap sw 0 0

#home
/dev/sda6 /home ext4 errors=remount-ro,discard 0 1

#storage
/dev/sdb1 /home/ross/storage ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#flash drive
/dev/sdc1 /home/ross/flash vfat iocharset=utf8,umask=000,user,noauto,exec 0 0

#external hard drive- this doesn't mount drive for some reason
/dev/sdc1 /home/ross/external ntfs-3g auto,exec,user,uid=1000,gid=100,dmask=027,fmask=137,utf8 0 0

#tmpfs
tmpfs /tmp tmpfs defaults,noatime 0 0
tmpfs /var/tmp tmpfs defaults,noatime 0 0
tmpfs /usr/src tmpfs defaults,noatime 0 0
tmpfs /var/cache/apt/archives tmpfs defaults,noatime 0 0
tmpfs /var/log tmpfs defaults,noatime 0 0

```


That's...odd. What's the output of ```
fdisk -l
```?

---

### Post by josephellengar on 2011-05-10
Right now I have the external drive plugged in and not the flash drive. fdisk -l output:

```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c001d45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        9827    78730240    7  HPFS/NTFS
/dev/sda3            9828       19457    77352975    5  Extended
/dev/sda5            9828       16355    52430479   83  Linux
/dev/sda6           16356       19457    24916783+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef43e130

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37190   298728643+   7  HPFS/NTFS
/dev/sdb2           37191       38913    13839997+  82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4661ceb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30402   244197376    7  HPFS/NTFS

```

---

### Post by blind2314 on 2011-05-10
> **josephellengar said:**
> Right now I have the external drive plugged in and not the flash drive. fdisk -l output:

```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9c001d45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26        9827    78730240    7  HPFS/NTFS
/dev/sda3            9828       19457    77352975    5  Extended
/dev/sda5            9828       16355    52430479   83  Linux
/dev/sda6           16356       19457    24916783+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef43e130

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37190   298728643+   7  HPFS/NTFS
/dev/sdb2           37191       38913    13839997+  82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4661ceb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30402   244197376    7  HPFS/NTFS

```

And if you have both plugged in and do that command, they both show as just /dev/sdc? Do you have more than one USB controller on your machine?

---

### Post by josephellengar on 2011-05-10
No. This is added to fdisk -l:
```


Disk /dev/sdd: 8220 MB, 8220835840 bytes
65 heads, 48 sectors/track, 5146 cylinders
Units = cylinders of 3120 * 512 = 1597440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5147     8028136    b  W95 FAT32

```

The flash drive automounted at /media/FLASH DRIVE because I had manually mounted the external hard drive at ~/flash

EDIT: I guess the problem is just that sometimes the drives are /dev/sdc and sometimes they are /dev/sdd because it is not consistent which is plugged in when since they are both external. Is there any way to identify the drive signature in the fstab so it knows exactly which drive is in and where to mount it?

---

### Post by blind2314 on 2011-05-10
> **josephellengar said:**
> No. This is added to fdisk -l:
```


Disk /dev/sdd: 8220 MB, 8220835840 bytes
65 heads, 48 sectors/track, 5146 cylinders
Units = cylinders of 3120 * 512 = 1597440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5147     8028136    b  W95 FAT32

```The flash drive automounted at /media/FLASH DRIVE because I had manually mounted the external hard drive at ~/flash

Ok..maybe I'm misunderstanding the requirement here, but just change your /etc/fstab line to mount the drive that will show up as /dev/sdd1 to the appropriate place. Since they're both *not* showing up as /dev/sdc1, which they shouldn't, there won't be duplicate entries. If you can't reliably determine which drive will be sdc and which will be sdd, use their UUIDs to mount them.


EDIT:  Yes, just use their UUIDs instead of their device path.

---

### Post by josephellengar on 2011-05-10
> **blind2314 said:**
> Ok..maybe I'm misunderstanding the requirement here, but just change your /etc/fstab line to mount the drive that will show up as /dev/sdd1 to the appropriate place. Since they're both *not* showing up as /dev/sdc1, which they shouldn't, there won't be duplicate entries. If you can't reliably determine which drive will be sdc and which will be sdd, use their UUIDs to mount them.


EDIT:  Yes, just use their UUIDs instead of their device path.

OK, how would I go about figuring out what there UUIDs are, and what is the syntax in the file if, for example, my external drive has UUID of 123 and I want it to mount at ~/external using ntfs and the other options I listed above?  Thank you very much for your help.

---

### Post by blind2314 on 2011-05-10
> **josephellengar said:**
> OK, how would I go about figuring out what there UUIDs are, and what is the syntax in the file if, for example, my external drive has UUID of 123 and I want it to mount at ~/external using ntfs and the other options I listed above?  Thank you very much for your help.

No problem. Run ```
blkid
```from a terminal with all the drives plugged in/mounted. It should return a UUID for each. Take this value and put it in your fstab like this:


```
UUID=12345 /home/ross/external ntfs-3g blah blah blah
```

The only part that changes is the first bit, where you change /dev/sdxx to be UUID=12345

---

### Post by josephellengar on 2011-05-10
> **blind2314 said:**
> No problem. Run ```
blkid
```from a terminal with all the drives plugged in/mounted. It should return a UUID for each. Take this value and put it in your fstab like this:


```
UUID=12345 /home/ross/external ntfs-3g blah blah blah
```

The only part that changes is the first bit, where you change /dev/sdxx to be UUID=12345

Thank you. Marking thread solved.

---

### Post by blind2314 on 2011-05-10
> **josephellengar said:**
> Thank you. Marking thread solved.


Glad I could help! :P

---

