---
title: "Ubuntu  10.10 doesn't recognize fat32 partition on sd card."
date: 2010-12-05
forum: General Help
---

### Post by -arturo- on 2010-12-05
I have a sandisk sd card with 3 partitions two ext2 and one fat 32 partition for some reson Ubuntu only automounts two ext2 partitions. I've tried inserting another card with only one fat32 partition and the system doesn't mount it. Both cards are visible in gparted byt not in "Places" menu.

---

### Post by -arturo- on 2010-12-06
This is my fstab file
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=5f97ed33-190d-4e3e-bea4-2ec8ab16dfae none            swap    sw              0       0

My fat32 sd card won't work with this setup...but if I add this line:
> LABEL="PENDRIVE" /media/external vfat defaults,user,dmask=027,fmask=137 0 0

My sd card in pendrive mounts in disk "External" but also the normal pendrive icon appears(As it was before I started experiencing this issue) so I can open my pendrive from both external disk and pendrive also my android phone fat32 partition finally mounts.

So after adding this line all my fat32 cards finally mount, now how can I setup fstab file so it won't mount specific partition "Pendrive" in this example but will mount all fat32 sd card partitions?

---

### Post by -arturo- on 2010-12-06
Any help please?

---

### Post by dcstar on 2010-12-06
> **-arturo- said:**
> I have a sandisk sd card with 3 partitions two ext2 and one fat 32 partition for some reson Ubuntu only automounts two ext2 partitions. I've tried inserting another card with only one fat32 partition and the system doesn't mount it. Both cards are visible in gparted byt not in "Places" menu.

Are you **100% sure** it is a FAT32 partition and **not** an exFAT partition?

---

### Post by -arturo- on 2010-12-06
> **dcstar said:**
> Are you **100% sure** it is a FAT32 partition and **not** an exFAT partition?

Thank you for your help dcstar.

Yes 3 am pretty sure that all my cards are formated to fat32. Actually i wasn't  aware that exFAT partitions even exist. I have used gparted and winxp native formatting program to format my sd cards to FAT32. Basically everything was working fine until recently the system stopped mounting Fat32 formated sd cards, maybe one of the. Recent system updates broke something.

---

