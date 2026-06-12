---
title: "How do I edit the Versions listed in GRUB?"
date: 2010-05-12
forum: General Help
---

### Post by Ichido on 2010-05-12
How do I edit the Versions listed in GRUB?
I have at least 25 different Versions listed in my GRUB Screen but they are not in the menu.lst !?
I only use 2 of them.

---

### Post by efflandt on 2010-05-13
Are you sure that you are still using legacy grub.  grub2 does not use menu.lst.  The correct way to eliminate old kernel files, which would drop them off of grub menus, is to remove the old kernel packages and header files (from Synaptic or however you normally do that).  Put "linux" in Quick search of Synaptic and scroll down.

---

### Post by 2hot6ft2 on 2010-05-13
Do you mean kernels?
You should always keep the 2 most current kernels that way if the newest one doesn't work right for some reason you have a working one to fall back to.

I used to say just remove the previous kernels but I have a little better understanding of it now and suggest you use the script provided here by Admin-Amir

[Upgrade to NEW Kernel - Clean the old.]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=4419")
:guitar:

---

### Post by Ichido on 2010-05-21
> **2hot6ft2 said:**
> I used to say just remove the previous kernels but I have a little better understanding of it now and suggest you use the script provided here by Admin-Amir

[Upgrade to NEW Kernel - Clean the old.]("http://forumubuntusoftware.info/viewtopic.php?f=7&t=4419")
:guitar:

Have you used this script?
Will it remove all of my Kernels or just some?
Thanks for your help.

---

