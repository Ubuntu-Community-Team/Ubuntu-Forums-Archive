---
title: "Screen resolution problem help needed asap"
date: 2010-10-14
forum: General Help
---

### Post by Alhenry on 2010-10-14
I have an hp vs17e monitor and I am running slax linux
But I have absolutely no idea how to fix the error resolution out of range on my computer monitor.it then shuts off and I can turn it back on and it'll do the same thing. Any help would be greatly appreciated and would also calm my mind

---

### Post by requeth on 2010-10-14
If your unable to get into the GUI then when Linux starts hold down Ctrl (I think) to get into grub boot loader. You can then choose to load Linux command line. Load command line and you have several options. The easiest generally if your a newbie is to sudo apt-get reinstall x11. This may hose things more but generally doesn't. Usually this will get you back into Ubuntu, but will likely require another reboot once you have things fixed to get the Ubuntu themes back working again. Alternately you can find which file in the x11 folder is storing your resolution and manually edit it and then reboot, but I always forget which file and half the time it requires a reinstall anyway. I'd do a command line backup of your data regardless.

---

