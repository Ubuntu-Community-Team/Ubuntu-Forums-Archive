---
title: "Need to repartition drive on VMware"
date: 2010-05-17
forum: General Help
---

### Post by bonesTdog on 2010-05-17
I am a Ubuntu newby running Lucid Lynx via VMware. I originally installed Ubuntu dedicating 20GB of hard drive space to VMware but now I need more space.  I increased the space allocation on VMware to 50GB but now need to repartition the drive for Ubuntu to use it.  Any help on how to do that?  Please use beginner terminology!  Thanks.

---

### Post by jbrown96 on 2010-05-17
Your partitioning in Vmware is probably fairly simple, so it should be easy. Please post the output of ```
sudo fdisk -l
``` and ```
mount -l
``` (those are lower case Ls, not ones)

You probably just need to run resize2fs but I can get the exact command after you run those commands.

---

### Post by bonesTdog on 2010-05-18
Thanks.  Here is the result. I have no idea what this tells me... I hope you do!

Disk /dev/sda: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e06b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2496    20049088+  83  Linux
/dev/sda2            2497        2610      915705    5  Extended
/dev/sda5            2497        2610      915673+  82  Linux swap / Solaris
bonestdog@ubuntu:~$ mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
gvfs-fuse-daemon on /home/bonestdog/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bonestdog)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by jbrown96 on 2010-05-19
All of this should be done within the Ubuntu guest.

1) you probably don't need swap and it should be removed. Swap should be taken care of by the host OS, not the guest. To turn it off ```
sudo swapoff -a
``` Then disable it forever by removing the swap line from /etc/fstab.
2) We need to delete your partitions using fdisk. This is not entirely secure, so backup any important data. ```
sudo fdisk /dev/sda
``` That will give you a fdisk prompt. Press p to print the current partitions. Then press d and the number of a parition that was listed. Repeat until all partitions have been delete (check with p again). 
3) Recreate your first partition. Press n to create, then p for primary, then 1, and enter twice to accept the default cylinders. Then w to exit.

4) You now need to reboot the VM. hold down shift at the very beginning of boot(make sure that the VM has keyboard focus) and you will get a Grub menu. Press e to edit the first entry. At the end of a long line is "splash" after that (space in between) add single, then press ctrl+x to boot. You will get a menu and choose root shell. 
5) Check the file system and enlarge it. ```
e2fsck -f /dev/sda1
``` and enlarge with ```
resize2fs /dev/sda1
``` Your disk is enlarged and you can reboot with ```
reboot
```

---

### Post by dcstar on 2010-05-19
> **jbrown96 said:**
> All of this should be done within the Ubuntu guest.

1) you probably don't need swap and it should be removed. Swap should be taken care of by the host OS, not the guest. To turn it off ```
sudo swapoff -a
``` Then disable it forever by removing the swap line from /etc/fstab.
........

[LIST=1]
[*]The guest VM knows absolutely nothing about resources on the host, so removing Swap will have the exact same effect as removing swap on any other system - it won't do it much good.
[*]Please put **all** VM issues in the Virtualization forum where they belong.
[/LIST]

---

### Post by jbrown96 on 2010-05-19
> **dcstar said:**
> [LIST=1]
[*]The guest VM knows absolutely nothing about resources on the host, so removing Swap will have the exact same effect as removing swap on any other system - it won't do it much good.
[*]Please put **all** VM issues in the Virtualization forum where they belong.
[/LIST]

Simply not true. That fdisk -l was done from within the guest, and the only information that could be returned are partitions created within the vm. That swap belongs exclusively to the guest and is not needed.

---

