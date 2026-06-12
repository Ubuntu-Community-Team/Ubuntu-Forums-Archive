---
title: "Grub restore and info"
date: 2009-12-13
forum: General Help
---

### Post by Nittalope on 2009-12-13
I'm experiencing some problems with grub.
I've partitioned my hard disk so to install windows vista, Ubuntu 9.10, OpenSuse and another Ubuntu 9.10 (test).
I mainly use the first Ubuntu installation, 9.10, then I installed Suse and its grub loader, then I installed the Ubuntu test and it's grub loader.
Now at start up I've got the grub list from the Ubuntu test installation, which means that it's not up to date with my main Ubuntu installation (the kernel should be the 2.6.31-16, but on the loader it's the -15 and thus is loaded!).
I tried installing grub2 using Synaptic in the main Ubuntu, but nothing changed. I checked with StartUp-Manager and the list of OSes I've got here is different from the one I've got at booting.

I would like to fix this (use the grub of my first Ubuntu) and, by the way, know how to check what is the grub in use at booting.
Grub2 version is1.97~beta4 (has checked with grub-install -v in the main Ubuntu).

Sorry if I'm not clear... but it's not clear...

---

### Post by Nittalope on 2009-12-14
Ok, I made the question, I found the answer.

Just reinstalled grub2 and grub-pc in the Synatpic Manager. And now I'm up with my updated grub list. Easy.

---

