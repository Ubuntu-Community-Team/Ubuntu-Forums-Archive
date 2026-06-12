---
title: "ubuntu uses only a small part of the disk"
date: 2012-04-01
forum: General Help
---

### Post by mavmic on 2012-04-01
hello

i am using Ubuntu for some time but i am still no expert . my installation uses 30 from the 130 GB the partition has. i am getting a message that only 1.4 GB remains empty and must clean disk. i want ubuntu to use the 100 free GB of the partition . is there any solution ?

thanks in advance for your help

---

### Post by coffeecat on 2012-04-01
> **mavmic said:**
> my installation uses 30 from the 130 GB the partition has.

That sounds as though you might have a wubi installation, in which you have a virtual partition for Ubuntu inside the Windows partition. Before we go any further we need to see whether you do indeed have a wubi install or not. In Ubuntu, open a terminal and post the output of:

```
mount
```

You can highlight the output with your mouse, right-click -> copy to paste it into your post.

---

### Post by papibe on 2012-04-01
Hi mavmic.

In order to give you a more grounded suggestion we would need more details about your disks and partitions.

Could you open a terminal and post the result of these commands?
```
sudo fdisk -l

mount -l

df -h
```
Regards.

---

### Post by mavmic on 2012-04-01
with mount i get the following and yes i did a wubi install from windows
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sda1 on /media/SYSTEM type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by mavmic on 2012-04-01
also i get
sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd403983d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       73979   594031517+   7  HPFS/NTFS
/dev/sda3           73980       91188   138231261    7  HPFS/NTFS
Partition 3 does not start on physical sector boundary.
/dev/sda4           91189       91202      105336    c  W95 FAT32 (LBA)

mount -l
/dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda3 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)
/dev/sda1 on /media/SYSTEM type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [SYSTEM]

&#931;&#973;&#963;&#964;&#951;&#956;&#945; &#945;&#961;&#967;&#949;&#943;&#969;&#957;            Size  Used Avail Use% Mounted on
/dev/loop0             29G   21G  6,8G  76% /
none                  2,7G  336K  2,7G   1% /dev
none                  2,7G  712K  2,7G   1% /dev/shm
none                  2,7G   88K  2,7G   1% /var/run
none                  2,7G     0  2,7G   0% /var/lock
none                  2,7G     0  2,7G   0% /lib/init/rw
/dev/sda3             132G   31G  102G  23% /host
/dev/sda1             199M   29M  171M  15% /media/SYSTEM

---

### Post by coffeecat on 2012-04-01
@mavmic, before we go any further, a side comment. You have your sda1 "SYSTEM" partition mounted in Ubuntu. That's your Windows 7 boot partition. My advice - don't mount it. Did you mount it by clicking on it in the left pane of a nautilus window, or does it mount on every boot (that is with a line in /etc/fstab)?

Your host partition is sda3 which looks as though it could be your Windows D: or E: partition. 30GB should be plenty for an Ubuntu partition if you store your personal files elsewhere. The easiest solution to your problem is to transfer any personal files you have in Your Ubuntu partition to the /host partition. Then the files would be accessible from Windows as well.

If you need to free up more space even after removing personal files, a start would be to run:

```
sudo apt-get clean
```

That will clear downloaded and cached package files and should free up a few hundred MB of space.

It is possible to increase the size of your wubi virtual disk, but I would suggest re-arranging where you store personal data first. See here:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_resize_the_virtual_disks.3F)

Also - I'm sure papibe will have some other suggestions. :)

---

### Post by papibe on 2012-04-01
That is indeed a Wubi install, as coffeecat predicted it.

Take a look at this tutorial: [HOWTO: Resize the WUBI virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371&highlight=resize2fs%20wubi").

Hope that helps.
Regards.

EDIT: look like racing with coffeecat today :)

---

### Post by coffeecat on 2012-04-01
> **papibe said:**
> 
EDIT: look like racing with coffeecat today :)

Cats and dogs? Who wins? :wink:

---

### Post by mavmic on 2012-04-01
the system partiton was mounted by my. i used gparted just to see what are my partitions . i have created a d partition but there is only one disk. i made a wubi install at this d partition. 
thank you for your suggestions and interest . i will try them .
best regards

---

