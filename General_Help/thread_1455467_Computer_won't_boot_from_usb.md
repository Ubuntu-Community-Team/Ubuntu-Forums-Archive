---
title: "Computer won't boot from usb"
date: 2010-04-16
forum: General Help
---

### Post by ttshivers on 2010-04-16
I have a very old computer that I want to install Ubuntu on. It does not have a CD drive so I have to install it on a USB disk. I used UNetbootin to put Ubuntu 9.10 on a USB disk, but the BIOS won't reconise the USB disk as a drive. I have looked at the other forum threads about this but really dont understand what they are talking about. I have a few USB disks that range in sizes from 256 MB to 8 GB. I put Ubuntu on the 1 GB USB disk. I have heard something about booting from a floppy or something like that. Just let me know if you need any more information about my hardware becuase I really don't know what to put.

---

### Post by marshmallow1304 on 2010-04-16
If the machine has a floppy drive, you should be able to use [PLoP Boot Manager]("http://www.plop.at/en/bootmanager.html") to boot from USB.

---

### Post by ttshivers on 2010-04-16
Would I do the PLoP Linux: Harddisk install using Floppy with a disk image?

---

### Post by marshmallow1304 on 2010-04-16
No need to install on the hard drive.  Simply write the floppy image to a floppy and boot from it.

---

### Post by quadproc on 2010-04-16
> **ttshivers said:**
> I have a very old computer that I want to install Ubuntu on. It does not have a CD drive so I have to install it on a USB disk. I used UNetbootin to put Ubuntu 9.10 on a USB disk, but the BIOS won't reconise the USB disk as a drive.
Your BIOS might be capable of booting from a USB drive - try the various function keys during the time between when the BIOS setup is offered and when the actual boot process starts.  I have an ASUS board with a somewhat buggy BIOS and I found that I had to use the F8 key to get a selection that included the USB drive.  Once I learned this then I could readily boot from USB drives.

If you just want to run an equivalent to the Live CD then a 1 GB USB drive is sufficient; if you want to do a full system install then you'll need more, probably 4 or 8 GB.

You might also consider Puppy Linux; it is relatively small both on disk and in memory.

quadproc

---

### Post by ttshivers on 2010-04-16
Wait, so these are the steps that I need to do in order to install the floppy?  [http://www.plop.at/en/bootmanager.html#runflp](http://www.plop.at/en/bootmanager.html#runflp)

> **marshmallow1304 said:**
> No need to install on the hard drive.  Simply write the floppy image to a floppy and boot from it.

---

### Post by ttshivers on 2010-04-16
I have tried all those tricks with the BIOS, but it still won't boot up directly from the USB disk.

> **quadproc said:**
> Your BIOS might be capable of booting from a USB drive - try the various function keys during the time between when the BIOS setup is offered and when the actual boot process starts.  I have an ASUS board with a somewhat buggy BIOS and I found that I had to use the F8 key to get a selection that included the USB drive.  Once I learned this then I could readily boot from USB drives.

If you just want to run an equivalent to the Live CD then a 1 GB USB drive is sufficient; if you want to do a full system install then you'll need more, probably 4 or 8 GB.

You might also consider Puppy Linux; it is relatively small both on disk and in memory.

quadproc

---

### Post by marshmallow1304 on 2010-04-16
> **ttshivers said:**
> Wait, so these are the steps that I need to do in order to install the floppy?  [http://www.plop.at/en/bootmanager.html#runflp](http://www.plop.at/en/bootmanager.html#runflp)

Yes

---

### Post by ttshivers on 2010-04-16
Thanks so much for all your help.

---

### Post by ttshivers on 2010-05-03
Lucid Lynx is now installed on that computer and is working fine!  Thanks for all your help again.

---

