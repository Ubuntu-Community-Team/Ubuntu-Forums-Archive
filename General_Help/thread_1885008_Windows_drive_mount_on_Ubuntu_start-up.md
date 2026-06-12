---
title: "Windows drive mount on Ubuntu start-up"
date: 2011-11-22
forum: General Help
---

### Post by Jimstehrman on 2011-11-22
Hey all,

I put ubuntu on my laptop recently, and set aside an NTFS partition for Windows, which I installed later (not the best choice, I know). So windows is installed and I fixed the GRUB and what not. Both boot with no issues. However on start up Ubuntu displays a message saying:
"The disk for /windows is not ready yet or not present"
followed by some options to skip or repair
/windows is the name of my windows partition, which up until recently was empty.
Is there a way to avoid this message? 

Thanks

---

### Post by ajgreeny on 2011-11-22
It sounds as if your /etc/fstab file is pointing to an incorrect partition UUID is causing the problem.  Can you please show the output of ```
sudo blkid -c /dev/null
``` and ```
cat /etc/fstab
```

---

### Post by Jimstehrman on 2011-11-22
Sure
```

sudo blkid -c /dev/null

```
yields:
```

/dev/sda1: UUID="A4B6B447B6B41C2C" TYPE="ntfs" 
/dev/sda2: UUID="3724-D000" TYPE="vfat" 
/dev/sda6: UUID="22b644d6-5413-4cfc-b1b0-19cff59fc4df" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="6e412935-dde1-4023-b78f-004d6d054b7c" TYPE="swap"

```

and
```

cat /etc/fstab

```
yields
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=22b644d6-5413-4cfc-b1b0-19cff59fc4df /               ext4    errors=remount-ro 0       1
# /common was on /dev/sda2 during installation
UUID=3724-D000  /common         vfat    utf8,umask=007,gid=46 0       1
# /windows was on /dev/sda1 during installation
UUID=4FD4-2E69  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda5 during installation
#UUID=b3b170dc-b238-4234-98dc-890e02cc9256 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

I see the problem...How can I change this?

Thanks!

---

### Post by Mark Phelps on 2011-11-22
Personally, I would remove the lines from /etc/fstab that mount your Windows partition.  Mounting that at startup is (IMHO) a bad idea in the long run.

---

### Post by ajgreeny on 2011-11-22
I agree with Mark, but none the less your fstab is pointing to a non-existent partition for windows, ie, the UUID entries are incorrect.

If you change the entry in fstab ```
4FD4-2E69
``` to ```
3724-D000
``` the error my disappear.

---

### Post by collisionystm on 2011-11-22
> **Jimstehrman said:**
> Hey all,

I put ubuntu on my laptop recently, and set aside an NTFS partition for Windows, which I installed later (not the best choice, I know). So windows is installed and I fixed the GRUB and what not. Both boot with no issues. However on start up Ubuntu displays a message saying:
"The disk for /windows is not ready yet or not present"
followed by some options to skip or repair
/windows is the name of my windows partition, which up until recently was empty.
Is there a way to avoid this message? 

Thanks


Lets keep it simple.

Install ntfs-config from the software center.

Run it. Its pretty self explanatory. Your problem will be solved in 30 seconds.

---

