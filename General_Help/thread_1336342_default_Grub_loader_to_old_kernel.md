---
title: "default Grub loader to old kernel"
date: 2009-11-24
forum: General Help
---

### Post by nanogeek on 2009-11-24
When I boot to a newer kernel I get video problems, where the mouse leaves black squares on the scree as it moves. When I boot into  kernel 2.6.24-21 from the grub menu this does not occur.

How can I set it so that the grub automagically boots 2.6.24-221 and I don't have to catch the escape into the grub menu at start up. This is especially crucial since my very old CRT monitor is not always on at that phase of boot up.

TIA
Nanogeek

---

### Post by cariboo on 2009-11-24
You can use startupmanager, which is in the repositories, to set boot order in grub.

---

### Post by dcstar on 2009-11-24
> **cariboo907 said:**
> You can use **startupmanager**, which is in the repositories, to set boot order in grub.

Or manually edit the /boot/grub/menu.lst file (probably easier to use the GUI app listed above - it does the edit for you).

---

### Post by nanogeek on 2009-11-25
> **cariboo907 said:**
> You can use startupmanager, which is in the repositories, to set boot order in grub.
That did the trick! Thanks, problem solved

---

