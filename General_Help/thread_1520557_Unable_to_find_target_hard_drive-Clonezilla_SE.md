---
title: "Unable to find target hard drive-Clonezilla SE"
date: 2010-06-29
forum: General Help
---

### Post by hotgrits on 2010-06-29
When attempting to restore disk or partition image taken from Computer A to Computer B I receive "Unable to find target hard drive: "sda". Check if this hard drive exists..."

The image was taken from Computer A via PXE boot and is stored in /home/partimag/ on DRBL/DHCP server running Ubuntu Server 10.04 (Clonezilla SE server setup per instructions at clonzilla.org). Computer A and B have identical hardware and image restores fine back onto Computer A. Running cat /proc/partitions on Computer B, after restore fails, displays same partition layout as Computer A - sda, sda1, sda2.

I'm hoping I'm missing a setting when starting Clonzilla for image restore.

---

### Post by gnijnew on 2010-11-29
Have you solved this problem? Could you please give me some tips about this issue?
It seems I met the exact the same problem as you described.

Thanks in advance.

---

