---
title: "How to detect and mount CD in Xubuntu?"
date: 2012-02-10
forum: General Help
---

### Post by ubuntu27 on 2012-02-10
Hello everyone. I have switched to **Xubuntu** from Ubuntu.
In Ubuntu, the CD mounted automatically, but it seems that it doesn't do that in Xubuntu.

If I try to mount I get:

```
ubuntu27@Computer:~$ sudo mount /dev/cdrom /mnt/cdrom
[sudo] password for ubuntu27: 
mount: mount point /mnt/cdrom does not exist
```


Here is the /etc/fstab:

```
Ubuntu27@Computer:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a63d808e-1f64-46f3-bbbf-592f695531e1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=9e3efa5e-2fef-4227-9e85-a440694f4719 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```


I don't know what else to do. Thank you guys.

---

### Post by btindie on 2012-02-10
> **ubuntu27 said:**
> ```
ubuntu27@Computer:~$ sudo mount /dev/cdrom /mnt/cdrom
[sudo] password for ubuntu27: 
mount: mount point /mnt/cdrom does not exist
```

As the message suggests, the mount point (directory) doesn't exist. Run the following first before running your command again.
```
sudo mkdir /mnt/cdrom
```

---

### Post by ubuntu27 on 2012-02-14
Hi btindie. Thanks for your help. :)

After today's Linux Kernel update (Kernel 3.0.0-16.28 ) in (X)Ubuntu, it now auto-mounts my DVD/CD drive. Guess it was a bug in Xubuntu.

[http://changelogs.ubuntu.com/changelogs/pool/main/k/kernel-image-3.0.0-16-generic-pae-di/kernel-image-3.0.0-16-generic-pae-di_3.0.0-16.28/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/k/kernel-image-3.0.0-16-generic-pae-di/kernel-image-3.0.0-16-generic-pae-di_3.0.0-16.28/changelog)


vfs: automount should ignore LOOKUP_FOLLOW
    - LP: #890952
  * VFS: Fix the remaining automounter semantics regressions
    - LP: #890952
* VFS: fix statfs() automounter semantics regression
    - LP: #890952
 * fs/9p: Fix invalid mount options/args
    - LP: #868628
 * Fix the conflict between rwpidforward and rw mount options
    - LP: #868628
  * Ecryptfs: Add mount option to check uid of device being mounted =
    expect uid
    - LP: #732628
    - CVE-2011-1833

---

