---
title: "swap shows up as 0MB but I allowocated 2.7GB for it"
date: 2010-12-05
forum: General Help
---

### Post by 55tptag on 2010-12-05
Hello,

I attached a picture showing a 2.7GB swap partition in the program named Disk Utility.  Also in the pic on the upper right is the program htop running and you see Swap is showing up as "Swp[ 0/0MB]".  And in the middle right is Sytem Monitor showing no swap space being used and that the swap space size is 0 bytes.

This all happened after resizing the partitions using gparted.  I resized all the partitions.  Part of what I did was increase the size of the swap partition from 512MB to 2.7GB.

But, as you can see, after rebooting the system no longer is using the swap space.  And it seems, according to the pic of System Monitor that there is no swap space.

Is there a way to fix this so Ubuntu will use the swap space?

Thank you.

---

### Post by sikander3786 on 2010-12-05
I would opt to see the output of these commands.

```
free -m
```

```
cat /etc/fstab
```

```
sudo fdisk -lu
```

```
sudo blkid
```

---

### Post by conradin on 2010-12-05
You dont want to be using the swap, its slower. Besides, your memory isnt fully used. 
Now, the real question is what happens when your computer is under load, as in a ton of processes going on.

---

### Post by kartabosh on 2010-12-05
it doesnt seam like the swap space is mounted

---

### Post by mcduck on 2010-12-05
Editing the partition changed it's UUID, so the system doesn't recognize the swap partition any more. The solution is simple, run "*blkid*" to list the correct UUID's for your partitions and then edit */etc/fstab* file to match those UUID numbers.

You will usually have to do this if you edit your partition layout in any way or format a partition, any such changes will result in the aprition getting a new UUID.

---

### Post by 55tptag on 2010-12-05
> **conradin said:**
> You dont want to be using the swap, its slower. Besides, your memory isnt fully used. 
Now, the real question is what happens when your computer is under load, as in a ton of processes going on.

I agree.  I would rather not be using swap.  So originally, I made my swap small; only 512MB.  And, I'm a desktop user and not running stuff like databases that are accessed by people or a website.  

But, I noticed that my swap was being used up to 512MB.  See the picture attached; though the picture only shows it using around 400MB.  I don't have a pic of it using 512MB.  

So, since it was using all the 512MB swap I decided to increase the size of the swap.  Maybe I could have left it alone?  But, I don't know enough about computers so I figured the easiest thing to do was simply add more swap space.

---

### Post by 55tptag on 2010-12-05
> **sikander3786 said:**
> I would opt to see the output of these commands.

```
brian@xps:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3522       3475         46          0        169       1076
-/+ buffers/cache:       2229       1292
Swap:            0          0          0
brian@xps:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=3e14fb19-d935-4f43-a82a-320d068d72fb /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=0f24fae1-135c-4750-9928-4632e2f04f45 /home           ext4    defaults        0       2
# /wd500 was on /dev/sdc1 during installation
UUID=f7c8af93-7b84-443e-b39b-982591ef46c9 /wd500          ext3    defaults        0       2
# /xtraSpace was on /dev/sda3 during installation
UUID=654d5c57-129b-4e06-92f1-673a8b4bcf56 /xtraSpace      ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=4655bf48-ffbe-43b5-aaf5-7121480d2ac7 none            swap    sw              0       0
brian@xps:~$ sudo fdisk -lu
[sudo] password for brian: 

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe785fb04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     5255167     2626560   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     5255168    33882111    14313472   83  Linux
/dev/sda3        33882112   156248063    61182976   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ac1eb53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009016e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux
brian@xps:~$ sudo blkid
/dev/sda1: UUID="578b2b8e-d1a6-4752-8bec-243b479e2b33" TYPE="swap" 
/dev/sda2: UUID="3e14fb19-d935-4f43-a82a-320d068d72fb" TYPE="ext4" 
/dev/sda3: UUID="654d5c57-129b-4e06-92f1-673a8b4bcf56" TYPE="ext4" 
/dev/sdb1: LABEL="/home" UUID="0f24fae1-135c-4750-9928-4632e2f04f45" TYPE="ext4" 
/dev/sdc1: LABEL="/home/brian/XTRL" UUID="f7c8af93-7b84-443e-b39b-982591ef46c9" SEC_TYPE="ext2" TYPE="ext3" 

```

---

### Post by oldos2er on 2010-12-05
> **55tptag said:**
> So, since it was using all the 512MB swap I decided to increase the size of the swap. 

Before doing that I would change the swappiness value. ```
gksu gedit /etc/sysctl.conf
``` and add **vm.swappiness=10** to the end of the file. More info here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by 55tptag on 2010-12-05
> **oldos2er said:**
> Before doing that I would change the swappiness value. ```
gksu gedit /etc/sysctl.conf
``` and add **vm.swappiness=10** to the end of the file. More info here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Thanks for the information.  
I would rather have tried this rather then blindly changing the swap partition size with gparted.  At least tried it for a few days and see how different values worked.  Then decide whether or not to change the swap size with gparted.

---

### Post by 55tptag on 2010-12-05
> **mcduck said:**
> Editing the partition changed it's UUID, so the system doesn't recognize the swap partition any more. The solution is simple, run "*blkid*" to list the correct UUID's for your partitions and then edit */etc/fstab* file to match those UUID numbers.

You will usually have to do this if you edit your partition layout in any way or format a partition, any such changes will result in the aprition getting a new UUID.

Thanks.  This solved the issue.

---

