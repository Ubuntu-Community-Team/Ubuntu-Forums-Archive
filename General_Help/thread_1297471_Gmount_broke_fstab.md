---
title: "Gmount broke fstab"
date: 2009-10-21
forum: General Help
---

### Post by wcGary83 on 2009-10-21
Hi everyone!

I ran Gmount-iso to run an iso file, but when I tried to unmount, it gave me a permission error and wouldn't unmount.  I ran gmount right from the applications->system tools.  

I thought nothing of it, but now when I boot I get warnings about fstab not being to mount, and my cdrom no longer mounts any media- great... I can't even burn a new live disk if I want to wipe my distro!

How do get fstab working again? (damn Gmount!!!)

Thanks!
Gary


edit: I tried changing the permissions of my cdrom-- sudo chmod 555 /media/cdrom0

Here's my fstab:

gary@g:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1ef88971-5c2e-4c63-9b99-969c55907aac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=6bd9386e-db1c-4b21-a25e-ea2c8e308254 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0


gary@g:~$ ls -lsh /media/cdrom0
total 0

---

