---
title: "extra kernals on grub"
date: 2010-01-23
forum: General Help
---

### Post by wcutrombonekid on 2010-01-23
so, every time i update my kernal, the old one remains on my grub menu when i boot along with the new one and all previous old ones.  I would like to get rid of all the old ones, I assume its just some setting i need to change.  Any help would be greatly appreciated.

I'm running Ubuntu karmic Koala with Grub 1, not 2

---

### Post by kimberlite on 2010-01-23
You can configure the number of kernel lines in your grub menu with "startup-manager" (go to "Advanced" tab). If you have not installed yet, you can install it with "sudo apt-get install startupmanager" command.

---

### Post by jflaker on 2010-01-23
I set mine, via startup manager, to retain 3 kernels....just incase an update goes buggy you can tell startup manager to always boot a specific kernel.

---

### Post by Yvan300 on 2010-01-23
You could install ubuntu-tweak which would allow you to remove all the old kernels.

---

### Post by wcutrombonekid on 2010-01-24
> **kimberlite said:**
> You can configure the number of kernel lines in your grub menu with "startup-manager" (go to "Advanced" tab). If you have not installed yet, you can install it with "sudo apt-get install startupmanager" command.

sweet, this got it.  i had changed it to show only one already in the startup manager, but i had forgoten to check the box that told it to acually do it.  thats why i was confused, thanks guys

thats all i got

---

