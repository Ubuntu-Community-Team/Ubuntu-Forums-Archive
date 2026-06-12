---
title: "Fat32 to NTFS trouble"
date: 2011-05-05
forum: General Help
---

### Post by rules on 2011-05-05
Hi all

I converted my D drive to NTFS today and now it does not auto mount when I boot up. I thought it would be as simple as changing the vfat to ntfs in fstab, but no :P

How do I fix this?

Thanks.

---

### Post by TeoBigusGeekus on 2011-05-05
Do you use UUIDs in your fstab?

---

### Post by rules on 2011-05-05
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4687c379-cd87-4dfb-a4da-bb41e94be937 /               ext4    errors=remount-ro 0       1
# /C-Drive was on /dev/sda2 during installation
UUID=BEA67931A678EAF3 /C-Drive        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /D-Drive was on /dev/sda4 during installation
UUID=4ACB-D8C7  /D-Drive        ntfs    utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=f0239a3c-ddc2-486d-b994-736938335d0c none            swap    sw              0       0





D DRIVE is the one I converted.

---

### Post by TeoBigusGeekus on 2011-05-05
The conversion has probably changed the UUID of the drive. Mount it and run
```
sudo blkid
```
to find it, then copy its value in your fstab.

---

### Post by rules on 2011-05-05
Thanks man, all sorted :)

---

### Post by TeoBigusGeekus on 2011-05-05
Brilliant!
Don't forget to mark the thread as solved.

---

