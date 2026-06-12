---
title: "HP ze5560us laptop gets to the grub menu only sometimes"
date: 2010-06-20
forum: General Help
---

### Post by mrflume on 2010-06-20
Not sure what's going on here, I installed the latest version of ubuntu on my old laptop which is an HP ze5560us and only sometimes will it get to the Grub menu for me to select ubuntu or XP. Any ideas as to why this would be happening? Once it gets into ubuntu it works fine but then sometimes I will come back home to find that the screen won't come back on and I will have to reboot. Any help would be appreciated greatly. Thanks in advance!

---

### Post by arrange on 2010-06-20
Sorry, I don't really understand - in the "the screen won't come back on" scenario you see the BIOS messages and then - ?

---

### Post by mrflume on 2010-06-20
like the screen will be black as if the screen went to sleep and if i try moving the mouse it won't bring me back to the desktop.

---

### Post by pi.theta on 2010-06-20
When you say that you get to the grub menu sometimes, what happens the rest of the time? Does it show an error or the comp doesn't start at all?

---

### Post by mrflume on 2010-06-20
it simple hangs at a black screen with the "_" just blinking and doesnt go to the grub menu so i have to just do a hard reset until it randomly  goes to the grub menu eventually...its very sporadic it seems

---

### Post by pi.theta on 2010-06-20
I am not certain about the part where the screen remains blank, but the grub problem could be due to the boot sector being corrupt. Try reinstalling grub manually by

```
grub-install --no-floppy --root-directory=/ /dev/sda
```

where /dev/sda tells it to install it to the mbr of the 1st hard drive

---

### Post by mrflume on 2010-06-20
ok when i did that from within ubuntu it said "cannot remove `//boot/grub/915resolution.mod': Permission denied

---

