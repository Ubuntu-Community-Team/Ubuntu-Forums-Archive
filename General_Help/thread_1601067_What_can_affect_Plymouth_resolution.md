---
title: "What can affect Plymouth resolution?"
date: 2010-10-19
forum: General Help
---

### Post by GeoMX on 2010-10-19
I have two Ubuntu installations: a full one and a light/custom. The full one has every default package installed using the Live CD and some extra packages I've been adding as I need them, the custom one is created using debootstrap and then I add some packages: xserver, fluxbox, alsa... among others.

But I have one problem: plymouth shows a low-res splash screen for the custom installation, while it works great with the full one. Both running on the same motherboard and with the same monitor. Besides, I need to set the FRAMEBUFFER=y option in the custom installation to make plymouth show the splash screen at boot.

I've tried setting GRUB_GFXMODE, GRUB_GFXPAYLOAD and GRUB_GFXPAYLOAD_LINUX for GRUB without any change, I'd like to know what other programs/drivers/configurations may affect Plymouth resolution so that I could find what is preventing my custom installation from showing a nice plymouth splash screen.

Thanks in advance for any comment.

---

### Post by GeoMX on 2010-10-26
Anything? Anyone?

---

### Post by lavinog on 2010-10-26
What video cards are they running.

Some video cards do not support KMS yet, which is needed for plymouth to display correctly.

---

### Post by Quackers on 2010-10-26
You said
"I've tried setting GRUB_GFXMODE, GRUB_GFXPAYLOAD and GRUB_GFXPAYLOAD_LINUX for GRUB without any change"
are you sure you changed the settings on the right system? If one system has been changed and the other hasn't and Plymouth shows a low-res screen then maybe your system is using the unchanged files to boot.

---

### Post by GeoMX on 2010-11-02
I'm sure I changed and updated the settings for the right system but will confirm and let you know.

Anyway, my full system does not need the "FRAMEBUFFER=y" option while the custom one does, if it is not set, the splash screen does not show, and this is with the same hardware. I'd like to know of any additional package that may affect Plymouth behavior so that I can add it to my custom install.

---

