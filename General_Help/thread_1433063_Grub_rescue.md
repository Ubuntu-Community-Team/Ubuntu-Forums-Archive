---
title: "Grub rescue"
date: 2010-03-18
forum: General Help
---

### Post by dayobiz on 2010-03-18
Pls i need help. I tampered with instalation process while i was re-installing ubuntu, now i have this command on my screen and i'm stuck.
 
GRUB RESCUE>_
 
PLEASE WHAT DO I NEED TO TYPE, FOR ME TO CONTINUE THE INSTALATION

---

### Post by mastermindg on 2010-03-18
grub-rescue>

The grub-rescue> mode is a more restricted subset of the grub> shell. Some commands are phrased differently here for easier use. Try help to start.

Useful tip: try to load normal mode: insmod /boot/grub/normal.mod

After this command help will show normal as possible command. Try it. Normal mode will be loaded. Now try to load ls (insmod /boot/grub/ls.mod), help and so on.

---

