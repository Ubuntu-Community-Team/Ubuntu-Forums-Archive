---
title: "How can i remove the grub loader?"
date: 2010-09-06
forum: General Help
---

### Post by BlackSwordD2 on 2010-09-06
had a dual booted laptop that i have removed XP from. now it still brings me to the boot menu how can i remove this so i will reboot into Ubuntu faster?

---

### Post by oldfred on 2010-09-07
Did you run this to eliminate the windows entry:

sudo update-grub

If it only sees Ubuntu it is supposed to by pass the menu and directly boot.

---

### Post by BlackSwordD2 on 2010-09-08
thank you, it didn't directly fix the problem but i was able to find the solution thanks to you

---

