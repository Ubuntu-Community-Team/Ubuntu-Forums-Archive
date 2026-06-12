---
title: "How to get PC to recognize Disk after HD?"
date: 2009-07-08
forum: General Help
---

### Post by setari on 2009-07-08
So I burnt Ubuntu to a disk, but my computer doesnt recognize the disk before booting the HD. How can I set it to do so, then change it back after I'm finished putting on ubuntu?

---

### Post by darolu on 2009-07-08
You need to set your CD/DVD ROM unit as the first booting device on your motherboard setup (like BIOS) How to do it, depends on your computer, each computer has a different way to access to this setup, many of them have a special boot-from-device menu that allows you choose before any boot loader (like grub) loads.
The way to bring either the setup (mostly bios) or the choose booting device menu is to press a key (or combination of keys) while the computer boots, usually when the vendor's logo shows.
The most common keys to access are "Del" (delete), F8 or F12; in some computers (like some HP ones) you need to press a combination like Control+F2, etc.

So, next time you turn your computer on, read all the information it gives you, usually the key or key combination is shown there; start pushing the key the loading screen tells you (or any of my suggestions) until you enter to the setup options, once you are there go to "Booting priority" or "Booting devices" or similar and set your CD ROM as first booting device and save changes. If you enter to a boot device choosing menu, you usually need to push a number only. Once you are done installing all you have to do is return to this set up program and change the booting order back to original values (or setting HD as first booting device).

BTW, as general rule, if you want more specific help and find your answer sooner; always include your system specs, like brand (if any), type of processor, memory, video card, etc.

I hope this helps and good luck.

---

### Post by darolu on 2009-07-08
Duplicated post. Mod/Admin please delete.

---

