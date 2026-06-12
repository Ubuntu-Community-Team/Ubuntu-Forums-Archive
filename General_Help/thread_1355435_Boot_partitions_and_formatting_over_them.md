---
title: "Boot partitions and formatting over them"
date: 2009-12-14
forum: General Help
---

### Post by PseudoLemon on 2009-12-14
My hard drive is laid out like this:
Windows partition /dev/sda1 (flagged as boot)
Extended partition /dev/sda2, inside is:
  Ubuntu /dev/sda5
  swap /dev/sda6

Basically, if I format the Windows partition, will grub have a fit or will something even worse happen?

---

### Post by dcstar on 2009-12-14
> **PseudoLemon said:**
> My hard drive is laid out like this:
Windows partition /dev/sda1 (flagged as boot)
Extended partition /dev/sda2, inside is:
  Ubuntu /dev/sda5
  swap /dev/sda6

Basically, if I format the Windows partition, will grub have a fit or will something even worse happen?

You can reinstall Grub either onto the MBR or another partition, but I think it will have to be on a Primary Partition to boot the system.

You may want to make some Primary Partition space on the drive, and Copy and Paste you Ubuntu partition into it.

---

### Post by PseudoLemon on 2009-12-14
Okay, so boot a liveCD, format Windows, then move Ubuntu to a new partition?

---

### Post by oldfred on 2009-12-14
Windows and possibly a few other systems use the boot flag and windows just about has to have a primary to boot from. Ubuntu does not use the boot flag and does not have to be in a primary partition. Deleting the windows partition may cause changes to UUIDs or partition numbers and that does change grub and fstab. Usually just deleting a partition should not change the other partitions but it depends exactly on what you do. Often the best choice is to reformat the partition and use it as a data partition for Ubuntu.

---

