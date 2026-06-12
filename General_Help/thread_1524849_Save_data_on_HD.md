---
title: "Save data on HD"
date: 2010-07-05
forum: General Help
---

### Post by d_darlac on 2010-07-05
Hi all, 

I have a 2nd partition in my HD that I use for saving all my data - the partition is in ntfs so I can use it with my windows virtual machine - 
Since day 1 I cannot save data in this partition under my windows VM, or even when using software through WINE
a 3rd small partition I have, has exactly the same settings as the main data partition and works fine

any ideas?

---

### Post by btindie on 2010-07-05
Is the 2nd partition mounted rw? Can you create normal files on it directly under Linux?
What's the output of
```
sudo fdisk -l
mount
```

---

### Post by d_darlac on 2010-07-05
Yes, I can create and save files under linux

here is the command output
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50f6e0a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122880000   83  Linux
/dev/sda2           15298       36333   168960000    7  HPFS/NTFS
/dev/sda3           36334       36940     4875727+  82  Linux swap / Solaris
/dev/sda4           36941       38913    15848122+   7  HPFS/NTFS
dimitris@dimitris-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4 on /media/xtra type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dimitris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dimitris)

---

### Post by Ocxic on 2010-07-05
changing a partition VirtualBox has direct access to outside of VirtualBox is a BIG NO, NO. 
It messes with the metadata that is created to keep track of changes, and accesses and can even prevent VirtualBox from using the partition at all.

---

### Post by d_darlac on 2010-07-07
HI, I fixed the problem by formating the partition - now works fine and I can share data between the host and guest OS

---

