---
title: "External hard drive won't show"
date: 2011-02-06
forum: General Help
---

### Post by ub45 on 2011-02-06
I have a 500GB Seagate HDD. It won't show in the computer folder area and I don't know what to do. I'm new to Linux. Could anybody help please this is becoming frustrating.

---

### Post by TeoBigusGeekus on 2011-02-06
Post us the output of
```
sudo fdisk -l
```
that's -L

---

### Post by ub45 on 2011-02-06
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d09c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9539    76614656   83  Linux
/dev/sda2            9539        9730     1533953    5  Extended
/dev/sda5            9539        9730     1533952   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c71bbdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by TeoBigusGeekus on 2011-02-06
I presume that your hard drive is /dev/sdb1.
It's just that it's not automatically mounted. 
Please confirm my last sentence by posting the output of
```
ls /media
```

---

### Post by ub45 on 2011-02-06
I've looked in the disk utility and it says the following 

device dev/sdb1

Partitioning master boot record

Partition type Linux (0x83)

As for ls /media nothing is showing

---

### Post by TeoBigusGeekus on 2011-02-06
Ok, we'll mount it by hand.
```
sudo mkdir /media/seagate
```
to create the directory on which your drive will be mounted and
```
sudo mount /dev/sdb1 /media/seagate
```
Does it show now in your media folder?

---

### Post by ub45 on 2011-02-06
Ok this is whats coming up. mkdir: cannot create directory `/media/seagate': File exists

---

### Post by TeoBigusGeekus on 2011-02-06
What? Can't be... You said that 
```
ls /media
```
didn't show anything...
Could you please repeat the command and post us the output?

---

### Post by ub45 on 2011-02-06
It just shows seagate thats it nothing else.

---

### Post by TeoBigusGeekus on 2011-02-06
```
ls /media/seagate
```
Does it list anything?

---

### Post by ub45 on 2011-02-06
No

---

### Post by TeoBigusGeekus on 2011-02-06
Ok, proceed with the mount command.

---

### Post by ub45 on 2011-02-06
Whats the coomand

---

### Post by ub45 on 2011-02-06
sorry  found the command nothing happening

---

### Post by TeoBigusGeekus on 2011-02-06
```
sudo mount /dev/sdb1 /media/seagate
```

---

### Post by ub45 on 2011-02-06
it says it does not exist

---

### Post by ub45 on 2011-02-06
correction, it's asking for file system type

---

### Post by TeoBigusGeekus on 2011-02-06
```
sudo mount -t ext4 /dev/sdb1 /media/seagate
```

---

### Post by ub45 on 2011-02-06
this is what is showing,

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by TeoBigusGeekus on 2011-02-06
Hm....
Looks like your drive has some errors...
Try 
```
sudo e2fsck -f /dev/sdb1
```

---

### Post by ub45 on 2011-02-06
Output,

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by TeoBigusGeekus on 2011-02-06
```
sudo e2fsck -b 8193 /dev/sdb1
```

---

### Post by ub45 on 2011-02-06
Output,

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by TeoBigusGeekus on 2011-02-06
Again?

---

### Post by ub45 on 2011-02-06
Forums won't allow me to show same output from last.

---

### Post by ub45 on 2011-02-06
I think this will not get fixed for the simply reason XP messed up everything when I was changing over to Ubuntu.

---

### Post by ub45 on 2011-02-06
Thanks for your time.............

---

