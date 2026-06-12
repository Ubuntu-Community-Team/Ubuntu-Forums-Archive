---
title: "hibernate not working"
date: 2012-03-23
forum: General Help
---

### Post by tobythedog on 2012-03-23
hi just upgraded to xubuntu 11.10 , hibernate wont work if i click hibernate machine does complete shut down anyone any ideas how to fix this please

---

### Post by plucky on 2012-03-23
> **tobythedog said:**
> hi just upgraded to xubuntu 11.10 , hibernate wont work if i click hibernate machine does complete shut down anyone any ideas how to fix this please

What size is your swap partition and does it work?

Post outputs for ```
free -m
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by subbu_ss on 2012-03-23
Doesn't work for me either.  Here is the output for my system.

[subbu@earth ~] free -m
             total       used       free     shared    buffers     cached
Mem:          7979       3884       4095          0        391       1405
-/+ buffers/cache:       2087       5891
Swap:         7609         22       7586


[subbu@earth ~] cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	nodev,noexec,nosuid	0	0
# / was on /dev/sda1 during installation
UUID=355c2248-a24b-4840-8000-e563ad9d0727	/	ext4	errors=remount-ro	0	1	# /dev/sda1
/dev/sda5	none	swap	sw	0	0
/dev/mapper/cryptswap1 none swap sw 0 0


[subbu@earth ~] sudo blkid
/dev/sda1: UUID="355c2248-a24b-4840-8000-e563ad9d0727" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="4e37b2d9-6807-49f3-a883-17ad9f7507b8" TYPE="swap" 

[subbu@earth ~] cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=4652ca99-97ad-4897-91de-d15669e50855

---

### Post by Toz on 2012-03-23
> /dev/mapper/cryptswap1 none swap sw 0 0
Hibernation to encrypted swap files does not work because the key to unencrypt the swap partition (that contains the resume image) is located in the encrypted partition.

Here is a link to a resource that shows how to revert to an unencrypted swap file (if you choose to go in that direction). ([http://www.logilab.org/blogentry/29155]("http://www.logilab.org/blogentry/29155"))

---

