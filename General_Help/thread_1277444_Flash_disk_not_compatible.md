---
title: "Flash disk not compatible"
date: 2009-09-28
forum: General Help
---

### Post by chrichion on 2009-09-28
Agorasa ena flashaki adata kai den to anagnorizi to ubuntu.Giati?

---

### Post by chrichion on 2009-09-28
I bought an adata flash disk and it can not be recognised by ubuntu. Do you know anything about it?

---

### Post by Giblet5 on 2009-09-28
How does it connect to the computer? USB? SATA? PATA? SCSI?

USB drives (are supposed to) all use the same methods. They should just work.

SATA/PATA/SCSI flash drives (aka SSD) have to be partitioned and formatted. ```
sudo fdisk -l
``` will show such a device if it's present.

---

### Post by credobyte on 2009-09-28
> **Giblet5 said:**
> How does it connect to the computer? USB? SATA? PATA? SCSI?

USB drives (are supposed to) all use the same methods. They should just work.

SATA/PATA/SCSI flash drives (aka SSD) have to be partitioned and formatted. ```
sudo fdisk -l
``` will show such a device if it's present.

Actually, there are a couple of Vista-certified USB Flash drives, which are incompatible with *nix's.

---

