---
title: "Edit Grub. Limited permissions!"
date: 2010-02-03
forum: General Help
---

### Post by jamoncillo on 2010-02-03
hi

I had to restore my grub after installing another distro

However, now that I want to edit my Grub it says my disc is read-only, therefore I can't make any changes

I just tried changing ownership first to my user, and then to root, and still I can't save the changes 

I was thinking in maybe changing the whole HDD ownership to root, and then switch my home folder's ownership back to my user

Any help/suggestions?? thanks!

---

### Post by jamoncillo on 2010-02-03
sss... after meddling for a while I managed to solve it

Sudo update-grub   (to fix my broken BT4 distro)

then 

sudo nautilus   and went to the grub folder, right clicked properties. I had ownership as root, but not permissions to read and write. Thanks

---

