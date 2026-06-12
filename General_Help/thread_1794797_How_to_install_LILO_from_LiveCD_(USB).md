---
title: "How to install LILO from LiveCD (USB)?"
date: 2011-07-01
forum: General Help
---

### Post by Pipps on 2011-07-01
**Background**
I am attempting to restore the MBR of a disc which comprises one 50GB Win XP partition (C:) and one c950GB NTFS partition (E:). Gparted confirms that the boot flag is set to C:. Fdisk confirms that the XP partition is sda1 and the other is sda2.

I boot into Ubuntu LiveCD from a 2GB USB pendrive. In order to do this, I am required to set the pendrive as the primary hard disc in the Asus mobo's BIOS. This is the only way to boot the machine from a USB device.

**Problem**
The problem arises when I try to run LILO in the usual way by performing the following two commands...
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

**Error**
At this point I am presented with the error message:
> Fatal: /dev/sda1 is not a master device with a primary partition table

**Question**
Is this because the aforementioned necessity of setting the pendrive in the BIOS as the primary disc, is somehow interfering with LILO?

How can I override this LILO error message and proceed with rewriting the MBR to sda1 regardless?

---

