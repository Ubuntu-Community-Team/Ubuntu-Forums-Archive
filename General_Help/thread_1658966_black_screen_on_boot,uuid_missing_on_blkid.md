---
title: "black screen on boot,uuid missing on blkid"
date: 2011-01-03
forum: General Help
---

### Post by linuxcss on 2011-01-03
running ubuntu 9.10 ... 
no recent updates were applied in over 3 months

after grub and before a login prompt ... systems shows
ubuntu splash screen and after about 30 seconds
a blank screen remains ... wait for like 5 mins and no change

so hit ctrl-alt-del and then select grub recovery entry,
get initramfs prompt and uuid id on root partition does not exist

if i run fdisk -l from initramfs i see the partition (/dev/sda6)
if i run blkid on /dev/sda6  no output is generated,

how can one regenerate a uuid for a given partition without reformatting?

---

### Post by tredegar on 2011-01-03
Are you at a root prompt? **blkid** needs to be run as root.
Try (as root) posting the output of **blkid /dev/sda***
Please also post the output of **cat /etc/fstab**

---

### Post by linuxcss on 2011-01-03
sudo blkid /dev/sda*
/dev/sda1: UUID="af35e71f-342b-4de2-92d6-711031851160" TYPE="ext3" 
/dev/sda5: UUID="30685d0f-f48a-451e-a3f6-6c101d89afce" TYPE="swap" 
/dev/sda7: UUID="c15383f4-7080-4de1-bbe5-fb9b5c9c898d" SEC_TYPE="ext2" TYPE="ext3" 

i got the following out of fstab (below) by booting to another partition
and mount /dev/sda6 using '/dev/sda6' and not the uuid

i also tried using
tune2fs -U 88165c1e-1cc3-47e6-a1e1-28d38cb324c6 /dev/sda6

but doing blkid still does not list anything for /dev/sda6


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=88165c1e-1cc3-47e6-a1e1-28d38cb324c6 /               ext3    errors=remount-ro 0       1
#/dev/sda6 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=c15383f4-7080-4de1-bbe5-fb9b5c9c898d /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=30685d0f-f48a-451e-a3f6-6c101d89afce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
~

---

### Post by tredegar on 2011-01-04
You can change fstab to use /dev/whatever, and comment out the UUID reference:
```
# / was on /dev/sda6 during installation
/dev/sda6 / ext3 errors=remount-ro 0 1
# UUID=88165c1e-1cc3-47e6-a1e1-28d38cb324c6 / ext3 errors=remount-ro 0 1
```

---

