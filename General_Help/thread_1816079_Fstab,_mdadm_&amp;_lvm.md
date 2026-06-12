---
title: "Fstab, mdadm &amp; lvm"
date: 2011-08-01
forum: General Help
---

### Post by oxsyn on 2011-08-01
Wondering about the proper FSTAB entry.
I've got a MDADM management raid 5 array.  
The entire raid is configured as an LVM2 physical volume.
The entire LVM2 PE is configured as an LVM2 Volume Group, named "lvm-raid."
The LVM2 VG contains a single logical volume named "lvm0."
LVM0 is formatted as an ext4 partition.

This leaves me with the following "virtual disks":

/dev/md0
/dev/lvm-raid/lvm0 -> ../md0
/dev/mapper/lvm--raid-lvm0 -> ../md0

I need to configure fstab to mount on boot lvm0 to /mnt/nas.  I've got several ways that I can create the stab entry, but I'm not sure which is right.  Any suggestions?

---

### Post by oxsyn on 2011-08-01
When I do ll /dev/disk/disk-by-uuid I see an entry for /dev/md0, but not the others.
When I do mount -l, I see /dev/mapper/lvm--raid-lvm0 on /mnt/nas/ type ext4 (rw)

---

