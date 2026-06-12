---
title: "Can't move files to 70 GB Filesystem..."
date: 2011-02-26
forum: General Help
---

### Post by ansionnachcliste on 2011-02-26
Hey guys, I've had Ubuntu since around November but I may have messed up and installed it a few too many times.

I've got 1 hard drive thats 320GB. 140GB is for Windows 7 but on Ubuntu when I got to 'Places' there is a 36 GB Filesystem and a 70 GB Filesystem. I'm running out of space on the 32 GB but I can't seem to write files to the 70 GB. When I try copy files from Windows 7 or Ubuntu onto it, it says: 

**Error while copying.**

The folder "University Work" cannot be copied because you do not have permission to create it in the destination.

It gives me three options to: Cancel, Skip or Retry. None of these solve the problem.

"University Work" is the folder I was using for an example.

What can I do as it is a terrible waste of space that I really need.

Thanks :)

---

### Post by blueridgedog on 2011-02-26
It would be helpful if you posted the output of

```
sudo fdisk -l 
```

and 

```
mount
```

---

### Post by ansionnachcliste on 2011-02-27
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1c6ddcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       20398   153605911    7  HPFS/NTFS
/dev/sda3           20399       38914   148723713    5  Extended
/dev/sda5           20399       24817    35491874   83  Linux
/dev/sda6           38157       38914     6079488   82  Linux swap / Solaris
/dev/sda7           29310       37790    68114432   83  Linux
/dev/sda8           37790       38157     2941952   82  Linux swap / Solaris
/dev/sda9           24817       29119    34555904   83  Linux
/dev/sda10          29119       29310     1527808   82  Linux swap / Solaris

Partition table entries are not in disk order

AND

/dev/sda9 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/graham/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=graham)


Thanks.

---

### Post by dcstar on 2011-02-28
> **ansionnachcliste said:**
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa1c6ddcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1]              1        1275    10240000   27  Unknown
/dev/sda2   *        1275       20398   153605911    7  HPFS/NTFS
/dev/sda3           20399       38914   148723713    5  Extended
[B]/dev/sda5           20399       24817    35491874   83  Linux
/dev/sda6           38157       38914     6079488   82  Linux swap / Solaris
/dev/sda7           29310       37790    68114432   83  Linux
/dev/sda8           37790       38157     2941952   82  Linux swap / Solaris[/B]
/dev/sda9           24817       29119    34555904   83  Linux
/dev/sda10          29119       29310     1527808   82  Linux swap / Solaris
..........

The highlighted partitions look like "leftovers" from previous installations and could probably be removed. Do this after removing them:

```
sudo update-grub
```

---

### Post by dcstar on 2011-02-28
> **ansionnachcliste said:**
> 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       20398   153605911    7  HPFS/NTFS
/dev/sda3           20399       38914   148723713    5  Extended
/dev/sda5           20399       24817    35491874   83  Linux
/dev/sda6           38157       38914     6079488   82  Linux swap / Solaris
/dev/sda7           29310       37790    68114432   83  Linux
/dev/sda8           37790       38157     2941952   82  Linux swap / Solaris
/dev/sda9           24817       29119    34555904   83  Linux
/dev/sda10          29119       29310     1527808   82  Linux swap / Solaris
.
All sizes are approximate:

/dev/sda1 = 10GB - probably "Recovery" partition
/dev/sda2 = 153GB Windows
/dev/sda5 = 35GB Linux
/dev/sda6 = 6GB Swap
/dev/sda7 = 68GB Linux
/dev/sda8 = 3GB Swap
/dev/sda9 = 34GB Linux ("root" partition)
/dev/sda10 = 1.5GB Swap

---

### Post by blueridgedog on 2011-02-28
You have two partitions from prior installs that are not mounted:

/dev/sda5 = 35GB Linux
/dev/sda7 = 68GB Linux

However, they are linux file systems, so if you want to use them you will need to format them and assign correct permissions to them.  You are failing now because of permission issues (I suspect) You can use gparted to manipulate them, or do it manually via the terminal (**you will erase the partitions with my steps, so use at your own risk and be careful**):

Wipe the partitions (skip this step if you simply want to mount them and see what is on them) **Mkfs is a partition format tool, use it carefully and verify that you have typed in the correct partition that you want to format**:
```
sudo mkfs /dev/sda5
sudo mkfs /dev/sda7
```

Make directories in your home folder to mount them (change USER to your user account - also storage1 and storage2 can be anything you want, just made up):
```
mkdir /home/USER/storage1
mkdir /home/USER/storage2
```

Mount the drives to your storage directories
```
sudo mount /dev/sda5/USER/storage1
sudo mount /dev/sda7/USER/storage2
```

Now that they are mounted, assign ownership to them:
```
sudo chown USER:USER /home/USER/storage1
sudo chown USER:USER /home/USER/storage2
```

If this were my system, I would remove the extra partitions and expand the /.

---

