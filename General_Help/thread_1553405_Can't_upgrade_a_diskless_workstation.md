---
title: "Can't upgrade a diskless workstation"
date: 2010-08-15
forum: General Help
---

### Post by Gibbon_99 on 2010-08-15
I have a mythfrontend box that boots diskless - everything works fine.  However, when attempting to upgrade the kernel - grub complains about not finding a device, and the upgrade fails.

How do I fix this?  Other packages upgrade with no problem.

thanks


```

The following partially installed packages will be configured:
  grub-pc linux-generic linux-image-2.6.32-23-generic linux-image-2.6.32-24-generic linux-image-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 1

```

This is /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
#/dev/nfs    /        nfs    defaults    1    1
/dev/nfs    /        nfs    intr,async,nfsvers=3,bg,actimeo=0,tcp,user    1     1

# /dev/sda5
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

/dev/nfs doesn't actually exist in the filesystem - but the machine still works.

---

### Post by dino99 on 2010-08-15
googling around about "diskless" it seems you need to upgrade from an other pc acting as a server

[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

or try to update from nfs:

[http://blog.crox.net/archives/29-Diskless-Ubuntu-Feisty-Fawn-NFS-install.html](http://blog.crox.net/archives/29-Diskless-Ubuntu-Feisty-Fawn-NFS-install.html)

---

