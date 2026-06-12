---
title: "Swap disables itself whenever I restart."
date: 2010-10-21
forum: General Help
---

### Post by ninjapirate89 on 2010-10-21
Title is self-explanatory. I turn on swap, restart, and it's off again. Ubuntu 10.10 64-bit. I tri-boot with Win7 (32-bit) and LMDE (32-bit) if it matters.

---

### Post by plucky on 2010-10-21
> **ninjapirate89 said:**
> Title is self-explanatory. I turn on swap, restart, and it's off again. Ubuntu 10.10 64-bit. I tri-boot with Win7 (32-bit) and LMDE (32-bit) if it matters.

You need to add it to /etc/fstab so that it is mounted at startup.

Open a terminal and post the outputs of ```
sudo fdisk -l
cat /etc/fstab
sudo blkid
```

---

### Post by ninjapirate89 on 2010-10-21
sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x626a9396

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12859   103186432    7  HPFS/NTFS
/dev/sda3           20340       38914   149197825    5  Extended
/dev/sda4           12859       20339    60082176   83  Linux
/dev/sda5           20340       21906    12582912   83  Linux
/dev/sda6           21906       38522   133467136   83  Linux
/dev/sda7           38522       38914     3145728   82  Linux swap / Solaris

Partition table entries are not in disk order

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7536e673-d420-4ccd-af31-6a2bc0733a50 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=fae56664-6957-4406-9986-3adef9203048 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=04b2f664-0efa-44c1-a69e-d1b5689fb9b9 none            swap    sw              0       0
# Hide System Reserved
/dev/sda1 none udf rw,noauto 0 0

```

sudo blk
```

/dev/sda1: LABEL="System Reserved" UUID="F0E228A1E2286DD2" TYPE="ntfs" 
/dev/sda2: LABEL="Win7" UUID="B0D62FDDD62FA298" TYPE="ntfs" 
/dev/sda4: LABEL="LMDE" UUID="e2a77c89-e07e-49a6-be7a-788046567688" TYPE="ext4" 
/dev/sda5: LABEL="Ubuntu Root" UUID="7536e673-d420-4ccd-af31-6a2bc0733a50" TYPE="ext4" 
/dev/sda6: LABEL="Ubuntu Home" UUID="fae56664-6957-4406-9986-3adef9203048" TYPE="ext4" 
/dev/sda7: UUID="04b2f664-0efa-44c1-a69e-d1b5689fb9b9" TYPE="swap" 

```

---

### Post by plucky on 2010-10-21
That looks normal for "swap" as far as I can see.

> Swap disables itself whenever I restart.

How are you monitoring this?
How do you know that swap is disabled?
Is there anything in the logs that might give you a clue?

What does ```
free -m
``` show?

---

### Post by ninjapirate89 on 2010-10-21
free -m
```

total       used       free     shared    buffers     cached
Mem:          2887       1466       1420          0         66        444
-/+ buffers/cache:        956       1930
Swap:            0          0          0

```

I'm using Conky to monitor swap and Gparted also shows it as disabled after I restart. Thanks for the help so far.

---

### Post by plucky on 2010-10-21
> Swap:            0          0          0

Definitely not working.

If there is nothing in the logs about the swap partition,it might be worth deleting the swap partition and re-creating it again in case there might be a bad block within the partition.
If you do so, the UUID of the partition might change,in which case you would have to alter the value in the /etc/fstab file to match whatever it says with the "sudo blkid" command.

Good Luck

---

### Post by ninjapirate89 on 2010-10-21
I'll give that a try. If it works I'll mark the thread as solved. Thanks again.

Edit: Didn't work. :(

---

### Post by VinDSL on 2010-10-21
Hrm...

You have rounding errors on Partition 1.

```
<snip>
Partition 1 does not end on cylinder boundary.
<snip>
```

Perhaps someone resized the disk, using GParted (or whatever), and didn't choose 'round to cylinders'.

I don't know how this would affect your swap partition, but...

Run this command, and check your boundaries:

```
sudo fdisk -lu

```

EDIT

I was just looking at your 'sudo fdisk -l' results.

```
255 heads, 63 sectors/track, **38913 cylinders**
```

```
Device Boot         Start       End       Blocks    Id  System

/dev/sda7           38522       **38914**     3145728   82  Linux swap / Solaris
```

The swap partition ends at cylinder number 38914, but the disk only has 38913 cylinders...

---

### Post by ninjapirate89 on 2010-10-21
> **VinDSL said:**
> 
Perhaps someone resized the disk

LOL, that 'someone' would be Windows. :P
Partition 1 is the "System Recovery" partition. I had no control over it when Windows installed.

Edit: Plus I think my desktop may be doing this too and it has only ubuntu on it. I haven't shutdown my desktop in a while to properly check it though.

---

### Post by VinDSL on 2010-10-21
> **ninjapirate89 said:**
> LOL, that 'someone' would be Windows. :P
Partition 1 is the "System Recovery" partition. I had no control over it when Windows installed.Aha!

Your system is infected with Windows...

That's the problem!  :D

---

### Post by ninjapirate89 on 2010-10-21
> **VinDSL said:**
> Aha!

Your system is infected with Windows...

That's the problem!  :D

XD Not that easy I'm afraid.

---

### Post by VinDSL on 2010-10-21
> **ninjapirate89 said:**
> XD Not that easy I'm afraid.How do your boundaries look?

---

### Post by ninjapirate89 on 2010-10-21
Maybe not being rounded to cylinders is the problem. My desktop isn't rounded either. I really don't want to reinstall all these OS's just to fix swap. Anybody know if there is a script I could use to turn it on after boot?

Edit: I could do 'swapon -a' in a bash script to run on startup but it needs to run as root.

---

### Post by VinDSL on 2010-10-21
If it was me...

I would try resizing (downsize) my swap partition, using GParted, and see if that fixes the problem.

---

