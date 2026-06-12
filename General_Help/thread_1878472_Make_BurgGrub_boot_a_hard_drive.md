---
title: "Make Burg/Grub boot a hard drive"
date: 2011-11-09
forum: General Help
---

### Post by Foxheadz on 2011-11-09
I have to hdd(s) in my computer one with ubuntu/windows and one with OS X lion. By default my computer boots the ubuntu/windows partition which has burg installed. Im trying to find a way to get burg to boot the second hard drive which has Chameleon boot loader for OS X. Anyone know how i can do this?

---

### Post by dcstar on 2011-11-10
> **Foxheadz said:**
> I have to hdd(s) in my computer one with ubuntu/windows and one with OS X lion. By default my computer boots the ubuntu/windows partition which has burg installed. Im trying to find a way to get burg to boot the second hard drive which has Chameleon boot loader for OS X. Anyone know how i can do this?

Create a custom menu entry that chainloads to the other drive (substitute burg for grub filenames):

[https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries](https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries)

---

