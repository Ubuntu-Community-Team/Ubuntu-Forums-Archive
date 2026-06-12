---
title: "USB Ubuntu MBR"
date: 2009-12-29
forum: General Help
---

### Post by Benster900 on 2009-12-29
I have a Toshiba laptop with Windows XP, and Ubuntu Wubi installed. I wanted too install Ubuntu on my flash drive. So, I put in a Ubuntu cd, and installed it on my usb. But my computer will only boot when the USB drive is plugged in. I want to remove that so that my laptop can boot without the usb drive.

P.S. Nice security feature.

---

### Post by lmarmisa on 2009-12-29
If you want to restore the Windows loader MBR, start Ubuntu from your pendrive or from a Live CD, open a terminal and type this command:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```If you restart your system, Windows will boot normally.

Best regards,

Luis

---

### Post by Benster900 on 2010-01-01
Thankyou SO much

---

### Post by fragos on 2010-01-01
Once your hard disk MBR is fixed run your BIOS to select the order of devices that are tried for booting. Then you'll boot from say a CD or USB if present.

---

### Post by dcstar on 2010-01-01
> **Benster900 said:**
> I have a Toshiba laptop with Windows XP, and Ubuntu Wubi installed. I wanted too install Ubuntu on my flash drive. So, I put in a Ubuntu cd, and installed it on my usb. But my computer will only boot when the USB drive is plugged in. I want to remove that so that my laptop can boot without the usb drive.


The Ubuntu install process assumes that you want Grub installed on the default hard disk (unless you manually change it in the Advanced Options - ?-).

Because you probably never changed this, it installed the Grub MBR on the hard drive but it was configured to load the USB - hence the system would not load up without the USB plugged in.

---

