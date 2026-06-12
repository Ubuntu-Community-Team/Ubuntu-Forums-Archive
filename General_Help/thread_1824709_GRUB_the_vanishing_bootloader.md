---
title: "GRUB: the vanishing bootloader"
date: 2011-08-14
forum: General Help
---

### Post by quequotion on 2011-08-14
here's a new one...

yesterday i turned on the pc, watched some videos, and turned it off.

today, it stops booting a little after  POST, as if there was no boot media.

i spin up the live cd and find my root partition exists, fsck finds no errors or bad blocks, but parted shows the boot flag and disk label are missing.

i reset the flag, the disk label, an reboot. No operating system. No GRUB.

on a hunch, I go back to the live cd, mount the root partition and install grub (sudo grub install /media/root/boot /dev/dm-1). one more reboot.

Back in business.

Where did GRUB go?
Why did it disappear?
How did it take the disk label and boot flags with it?

My root drive is on a RAID:0, running on the AMD 890FX chipset. Somehow, I think my MBR must have been erased. I don't understand how or why that would happen *without catastrophic data loss* and without any system setting changes.

---

### Post by quequotion on 2011-08-21
This happened again.

Same solution, from the livecd **sudo grub-install --boot-directory /media/root/boot /dev/dm-1** (now without type-o!).

Why does grub sometimes disappear?

Is there a way to prevent this?

---

