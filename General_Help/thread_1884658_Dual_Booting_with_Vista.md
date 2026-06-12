---
title: "Dual Booting with Vista"
date: 2011-11-21
forum: General Help
---

### Post by bgray0285 on 2011-11-21
I installed ubuntu on its own partition and had select to run it and windows side by side and to be able to select which I wanted to run at start up, but when I start my computer I get no options and windows starts every time.

---

### Post by Mark Phelps on 2011-11-21
Next time you boot, hold down a SHIFT key -- and see if you get a GRUB menu.  

If you don't, are you sure you didn't install using Wubi -- from inside Windows?

---

### Post by newbie-user on 2011-11-21
When you installed Ubuntu, did you install GRUB to the boot loader?  If you didn't, then GRUB won't run when the computer starts and you won't get an option of which OS to start.  The Windows boot loader is loaded instead, which doesn't have any information about how to boot Ubuntu.

---

### Post by bgray0285 on 2011-11-21
How do I install GRUB to the boot loader ? I did not see an option for this during the intallation

---

### Post by Mark Phelps on 2011-11-22
You don't NEED to install GRUB; that is installed automatically when you install Ubuntu.

Go back to my first post and read what I wrote...

IF you see a GRUB menu, it IS already installed.

---

### Post by alphaamanitin on 2011-11-22
It isn't always  installed automatically.  Well, splitting hairs, it is the default option, so think back did you unselect install GRUB?  If not, take Mark's first post.  

AlphaA

---

### Post by Linuxratty on 2011-11-22
If you installed Ubuntu first and then Windows,Windows won't see anything but itself.
Always install Windows first. Ubuntu will see it.

---

