---
title: "Stucktin Command in (initramfs)"
date: 2009-09-19
forum: General Help
---

### Post by jenova_skill on 2009-09-19
I just updated the headers or something and I kept the old ones instead of replacing them. Now I boot strait to (initramfs) 

ALERT! /dev/disk/by-uuid/............   Does not exist. Dropping to Shell!

---

### Post by arrange on 2009-09-19
If you boot into an older kernel, do you see the same error?

---

### Post by jenova_skill on 2009-09-19
yea..... I tried to go into safe mode and same thing

---

### Post by jenova_skill on 2009-09-19
Wait i just tried it on the older 1 and it works .....How can i fix it where they all work now?

---

### Post by arrange on 2009-09-19
> **jenova_skill said:**
> Wait i just tried it on the older 1 and it works .....How can i fix it where they all work now?
Then I don't know :) You can try and change the kernel line in the Grub menu: press 'e' when you see the menu, and change the kernel line (you have to press 'e' again) from *root=UUID=blablabla* to *root=/dev/sda3* (change /dev/sda3 to your actual partition with Ubuntu). Then 'b' for booting.

---

