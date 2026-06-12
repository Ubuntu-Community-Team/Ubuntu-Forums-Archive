---
title: "Installing Xubuntu on a PC that has a broken cd rom &amp; won't boot from usb"
date: 2009-11-29
forum: General Help
---

### Post by cutman on 2009-11-29
Ok this is kind of a weird situation. My younger brother wants me to turn his old PC into a Linux machine, but there are some problems: his CD-Rom doesn't work plus I can't seem to get it to boot from the USB flash drive. I created a bootable USB of Xubuntu 9.10. Maybe I overlooked something, but I couldn't find a solution in the BIOs of this machine, an HP Pavilion xt963 desktop with Win XP home Edition. His XP is full of viruses and spyware so he wants a clean start. Is there any way I can install the OS without getting a new CD-Rom?

---

### Post by rudy.b on 2009-11-29
I ran into a similar situation installing Ubuntu on an old laptop.  Fortunately the machine was so old that it had a 3.5" floppy drive built in, so I booted with the [PLoP Boot Manager]("http://www.plop.at/en/bootmanager.html") on a floppy which allows the user to select a USB device even though the BIOS didn't support booting from USB.  I followed the instructions in the section titled "[Run from Floppy with a disk image]("http://www.plop.at/en/bootmanager.html#runflp")" to get the boot manager on the floppy, and then boot the old machine from the floppy.

By the way, if you find that Xubuntu is too heavy for your old HP, check out this wiki page for some useful alternatives for installing Ubuntu: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Meskarune on 2009-11-29
you could always see if you can borrow an external cd drive from someone...

---

