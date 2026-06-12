---
title: "changing console size"
date: 2009-08-26
forum: General Help
---

### Post by Keith Hedger on 2009-08-26
after switching to a virtual terminal via ALT-F1 etc I would like to increase the resolution of the console from the standard 80 columns any ideas?

---

### Post by CatKiller on 2009-08-26
You can do this by increasing the resolution of the framebuffer device by passing a vga parameter to the kernel in GRUB's menu.lst.

Pick one of the [mode numbers]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Other_commonly_available_modes") for the resolution and colour depth that you want. Not all modes are available for all video cards; the modes that are available over the VESA spec are entirely at the discretion of the video card manufacturer.

As an example, I've got **vga=0x31B** in the kernel line of /boot/grub/menu.lst which gives me 1280×1024@24-bit for my virtual consoles.

---

### Post by Keith Hedger on 2009-08-27
Thanks for the link the info in it works perfectly :):)

---

