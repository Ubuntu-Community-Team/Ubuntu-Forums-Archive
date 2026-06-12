---
title: "Grub configuring menu.lst wrong..."
date: 2006-06-16
forum: General Help
---

### Post by Morientes on 2006-06-16
When I installed Ubuntu 6.06 it configures my menu.lst wrong. F.ex it said that Ubuntu should boot from hd(1,2) when the right entry is hd(3,2).
Now whenever I update my kernel it happens again and I have to change it manually!
Is there any way I can fix this? Breezy did not do it..

---

### Post by caldevil on 2006-06-16
In the menu.lst search for the line containing groot=(hd1,2). Change it to (hd3,2). Do not uncomment the line and then run 'sudo update-grub'

---

### Post by Morientes on 2006-06-17
Ok, thanks...

---

### Post by jakeee on 2006-06-17
I have a problem with grub too. Everytime I install a new kernel the initng option gets deleted. How do I prevent this?

---

