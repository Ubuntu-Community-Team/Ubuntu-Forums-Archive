---
title: "Bootloader using bluetooth - HELP!"
date: 2006-06-02
forum: General Help
---

### Post by Everglow on 2006-06-02
I've set up a dual-boot for Windows XP and Ubuntu 6.06 using the automatically created bootloader provided in the Ubuntu install.  The problem is that I only have a bluetooth keyboard mouse combo.  How do I configure the bootloader to recognize bluetooth so that I can select my OS?

---

### Post by garyng on 2006-06-02
I don't think you can, neither in XP's loader or GRUB. Even USB can be problematic.

---

### Post by Skye on 2006-06-02
Unfortunately, I think garyng is right.  Bluetooth drivers aren't loaded in Ubuntu until the ending part of the driver loading process, which indicates that they won't work until the drivers are loaded.

But then again, that doesn't make sense- how would one access the BIOS if the computer couldn't access the keyboard until the OS is loaded?

Does anyone else have any input on this?

---

### Post by garyng on 2006-06-02
[QUOTE=Skye]Unfortunately, I think garyng is right.  Bluetooth drivers aren't loaded in Ubuntu until the ending part of the driver loading process, which indicates that they won't work until the drivers are loaded.

But then again, that doesn't make sense- how would one access the BIOS if the computer couldn't access the keyboard until the OS is loaded?

Does anyone else have any input on this?[/QUOTE]

My limited understanding(on most PC anyway) is that the BIOS only supports the ancient 8042 interface. Some newer one does include support for USB(and you can't randomly pick which USB port to plug the keyboard). Bluetooth is a no way, just curious if MacIntel supports bluetooth keyboard before boot.

---

### Post by Everglow on 2006-06-02
Are there any in-system boot loaders that will allow me to use my bluetooth?

---

### Post by Everglow on 2006-06-07
Bump?

---

