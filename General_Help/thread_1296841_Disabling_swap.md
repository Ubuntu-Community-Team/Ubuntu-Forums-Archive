---
title: "Disabling swap"
date: 2009-10-21
forum: General Help
---

### Post by Aero-Z on 2009-10-21
Hello,

I got about 3GB of RAM and about the same amount of Swap space.
The thing is that I never use the Swap.
Can anybody guide me how to disable Swap and add the swap space to my "/" partition?

Thanks.

Added picture of gParted.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=348f19af-4ba2-4ab3-b31f-0a1faaf0e6ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01ebe1b8-1457-4248-b3fd-1c50b8b386f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by P4man on 2009-10-21
boot from a live cd
start gparted (partition editor)
Right click swap and select swapoff
Delete the swap partition and then the extended partition it is contained in
resize /

---

### Post by Aero-Z on 2009-10-21
> **P4man said:**
> boot from a live cd
start gparted (partition editor)
Right click swap and select swapoff
Delete the swap partition and then the extended partition it is contained in
resize /
That was easy, thanks :)

But now I got to do some changes in fstab. It looks like this at the moment:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=348f19af-4ba2-4ab3-b31f-0a1faaf0e6ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=01ebe1b8-1457-4248-b3fd-1c50b8b386f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Just have to remove the line starting with UUID under "swap was" line?

---

### Post by egalvan on 2009-10-21
> **Aero-Z said:**
> That was easy, thanks :)

But now I got to do some changes in fstab. It looks like this at the moment:

Just have to remove the line starting with UUID under "swap was" line?

Placing a # at the front of the line is enough.
This will remind you of what you had.

But yes, deleting that line will work.

---

### Post by Aero-Z on 2009-10-21
> **egalvan said:**
> Placing a # at the front of the line is enough.
This will remind you of what you had.

But yes, deleting that line will work.
Yup, got it to work. I just made a backup of the file :)

---

