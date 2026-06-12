---
title: "oops... error 17 at boot"
date: 2010-02-23
forum: General Help
---

### Post by flyingsliverfin on 2010-02-23
i was just playing around on my flash drive's ubcd, and i started something called trinux (i had no idea so i started it). It was was a command line like program. In there, there seemed to be a file called hdb0, which i tried to ls into... nothing happened. When i couldn't shut down, i just used the power button.
when i booted up again, i entered grub, but then i couldnt boot my windows partition or my ubuntu one.

i think the exact error was:
error 17: unable to mount partition   -   for ubuntu. i really want to get this running again.

doing this from a memory stick wtih 8.10, so it cant read ext4 systems. Im burning a 904 cd that can read it and see if its possible to mount my hdd

---

### Post by wojox on 2010-02-23
I had that problem once and this helped me out [grub-error-17]("http://stringofthoughts.wordpress.com/2009/05/24/grub-error-17-debianubuntu/")

---

### Post by flyingsliverfin on 2010-02-23
im not sure if its a grub error 17... it didnt say grub. just error 17

---

### Post by flyingsliverfin on 2010-02-23
found out some more stuff:

my windows partition come up with:
error 13: invalid or unsupported executable format

my exact ubuntu error is:
error 17: cannot mount selected partition.

also, ubuntu 810 keeps trying to mount my windows partition (which is ntfs) as ext4!!!!  Could this have to do with the MBR?

i tried to manually force the ntfs to mount using mount -t ntfs /dev/sda1 windows force   then it says that the ntfs signature is missing...

any new help?

---

