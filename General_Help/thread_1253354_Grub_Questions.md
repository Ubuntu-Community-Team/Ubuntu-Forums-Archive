---
title: "Grub Questions"
date: 2009-08-30
forum: General Help
---

### Post by holycow131415 on 2009-08-30
How often does it back up or make a linux-image. Im not sure if i understand too well. package manager has newer linux-images, so should you download these if grub backs up for you? Im just wondering because i had to remove some linux-images because my sound got corrupt some how and using a backup image solved my problem lol.

---

### Post by jerrrys on 2009-08-30
grub is not a backup tool; you can use it to go back to previous kernel.  you can also install **startup manager** in synaptic to keep track of kernels...

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by nhanquy on 2009-08-30
Grub is just a boot loader. It's a program the machine runs first to bring up other programs after that. And the programs after Grub you would call the OS.

So Grub has nothing to do with backups.

When you update/upgrade Linux you might end up with a newer kernel and it shows up as an option in the grub menu list. The software upgrader does that so Grub would  know how to boot the new kernel.
Grub does not backup anything. 

If you don't like a newer version or a too old version you can delete those options out of the list. As well you can delete those under /boot directories.

Read GRUB manual for more information.
Good luck!

---

