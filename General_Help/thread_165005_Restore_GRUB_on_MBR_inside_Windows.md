---
title: "Restore GRUB on MBR inside Windows?"
date: 2006-04-23
forum: General Help
---

### Post by lezz on 2006-04-23
Hi

Is it possible to restore GRUB on MBR from Windows? That is, I dont want to restore it with a floppy disc or from Linux. I has to be done from Windows XP.

Any ideas?

---

### Post by Kethinov on 2006-04-23
Why not just restore it from a Linux LiveCD?

---

### Post by rado_london on 2006-04-23
Would you share the reasn of choosing nearly imposible way for completing that kind of task.

---

### Post by Kethinov on 2006-04-23
I suppose it might be possible with Cygwin.

---

### Post by lezz on 2006-04-23
[QUOTE=rado_london]Would you share the reasn of choosing nearly imposible way for completing that kind of task.[/QUOTE]

cause my laptop has no floppy reader, nor a cd-rom. each time i wanna reinstall windows it has to be through a pxe-installation. but this is not an option while im travelling. i have made it possible to install windows using grub booting the laptop from a virtual floppy image. but during the windows installation, it will have the mbr restored and i cant use grub to install windows again when i need to. the only option for me is beeing able to restore the mbr with grub inside windows.

i will try cygwin. in the mean time tell me if you got some more ideas.

---

### Post by rado_london on 2006-04-24
I would recommend you Live distro on usb port. Good examples can be Slax and Damn Small Linux. Just boot it and restore grub.

Hope this helps

---

### Post by Amped-Gaming on 2006-04-24
Yup, just go with DSL (Damn small linux) and restore grub, that should work fine ..

---

