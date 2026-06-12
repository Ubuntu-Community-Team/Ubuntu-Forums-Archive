---
title: "Unable to access files on mounted NTFS"
date: 2011-11-27
forum: General Help
---

### Post by Vapourstreak on 2011-11-27
Hey,

I'm using an NTFS partition to store my data on my Ubuntu installation, so I've set it to automount in a empty folder inside my Home folder.  This configuration worked before, but suddenly after an install of some application, don't know what, it's not showing up.  It's showing up as a mounted partition in Nautilus and using the 'mount' command, but when I navigate to the mounted partition, there aren't any files inside it.  

To get my files back, I have to run

> sudo umount /dev/sda3
which gives me "umount: /home/dk-/data: not mounted"
then
> sudo mount -a

After running those commands, I'm able to see my files again.

My fstab:
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6be4242d-74ac-4d4b-9b81-a264b816b97c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=609f4b79-f7f2-4742-a0aa-415fc22a1f6a /boot           ext2    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=8c5e4100-6100-4ef4-9db1-6ca8f3ee62e6 /home           ext4    defaults        0       2
# ntfs partition was on /dev/sda3 during installation
UUID=6AC82468C82434AB /home/dk-/data           ntfs-3g    defaults        0       0
# swap was on /dev/sda5 during installation
#UUID=daf937b9-d607-429d-9d15-de87967934bb none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

I've tried different options such as
> gid=users,umask=0022
> gid=users,fmask=113,dmask=002
> uid=USERNAME,gid=users

As well as different folders within my home folder.


EDIT: Forgot to add that even when I delete the partitions line from fstab, it still gets mounted upon login.  My hunch is that some other application is mounting it before fstab is.  Don't know if that's possible though.

Could anyone help me out?

Thanks.

---

### Post by Vapourstreak on 2011-11-27
Bump.  Help please.

---

### Post by Vapourstreak on 2011-11-27
.

---

