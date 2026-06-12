---
title: "Trying to QEMU Windows"
date: 2006-04-15
forum: General Help
---

### Post by Mazin on 2006-04-15
I'm trying to run windows xp in QEMU, but instead of creating a image file and installing it, can I run it off disk?

I already have winxp installed on another hard drive (ntfs), and I want to boot it from there - is that even possible?
I'm running something like:

qemu -hda /dev/hda1 -boot c [-snapshot]

where hda1 is my unmounted windows harddrive.

---

### Post by PriceChild on 2006-04-15
Nope... i think is the short answer :)

---

