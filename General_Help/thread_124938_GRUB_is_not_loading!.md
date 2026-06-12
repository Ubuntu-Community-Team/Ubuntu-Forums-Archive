---
title: "GRUB is not loading!"
date: 2006-02-02
forum: General Help
---

### Post by Zalbor on 2006-02-02
I reinstalled windows XP, so I needed to replace GRUB. I entered the installation program for ubuntu, mounted all partitions as they were before and without formatting, and reinstalled GRUB (this method has worked until now).
Now when I reboot it says "GRUB level 1.5, loading GRUB" and the cursor keeps flashing, but there's no disk activity and nothing happens. It was loading right away before now. What could be wrong this time?

By the way, I also have win98 installed, on a separate hard drive, and that's where the XP installation put the boot program. That's where I'm trying to install GRUB too, but I tried the other drive as well and the same thing happens.

---

### Post by lysis on 2006-02-02
did you write to MBR?

---

### Post by Zalbor on 2006-02-02
As far as I know, that's what it did. It's the automatic ubuntu installation anyway.

---

### Post by Zalbor on 2006-02-02
Anyone?

---

### Post by Zalbor on 2006-02-03
I really need some help with this... There is no error code or anything to tell me what's wrong.

---

### Post by cotcot on 2006-02-03
Why do you install the grub boot loader on the win 98 disk ?
Obviously the grub bootloader does not find stage 1.5 normally in /boot/grub/ of ubuntu.
Have you tried to install the grub bootloader on the XP drives MBR ?

---

### Post by Zalbor on 2006-02-03
[QUOTE=cotcot]Why do you install the grub boot loader on the win 98 disk ?
Obviously the grub bootloader does not find stage 1.5 normally in /boot/grub/ of ubuntu.
Have you tried to install the grub bootloader on the XP drives MBR ?[/QUOTE]
I install it on the win98 disk because that's where the installation puts it by default (IDE disks come before SATA). I tried to install it on the other disk too, but it's all the same.

However, it seems to be a problem with my computer hardware, possibly the SATA disk. I tried to install XP again, and the installation program froze at the very beginning. When I disabled the IDE disk through BIOS, it worked. When I disabled both disks, it worked again, but only seeing the SATA one.
After reinstalling XP on that one, it still wouldn't boot. But XP booted from the IDE disk's MBR (I had used fixmbr in the meanwhile) and 98 still boots from there...
But if it's a problem with the SATA's mbr, why didn't grub work from IDE?

The above is just rumblings, as it might not be a problem with grub after all...

---

