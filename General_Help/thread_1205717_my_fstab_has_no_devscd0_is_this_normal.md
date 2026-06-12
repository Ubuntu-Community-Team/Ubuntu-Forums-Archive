---
title: "my fstab has no /dev/scd0 is this normal?"
date: 2009-07-06
forum: General Help
---

### Post by poliltimmy on 2009-07-06
I notice my fstab has no /dev/scd0 is this normal? I have 2 Rom drives One combo and one DVD burner.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda6 during installation
UUID=18746631-5750-47a3-b856-af4a1b91c17d / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda7 during installation
UUID=7daa624c-1823-417a-ba0f-e6723c8e0a31 none swap sw 0 0
/dev/scd1 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
poliltimmy is online now Report Post   	Edit/Delete Message

---

### Post by del_diablo on 2009-07-06
Its more than normal.

---

### Post by poliltimmy on 2009-07-08
Ok just looked odd to me. I'm still learning! Thanks.

---

