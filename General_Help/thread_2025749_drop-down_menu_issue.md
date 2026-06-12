---
title: "drop-down menu issue"
date: 2012-07-14
forum: General Help
---

### Post by hotshot247 on 2012-07-14
hey, i'm using ubuntu 12.04 with the gnome-shell desktop environment and i noticed that everytime i click a drop-down menu, i can see what's in the menu but it won't let me choose anything else but what's already chosen. is this a bug with gnome-shell? is their a way to fix it? thanks in advance for the help!

---

### Post by OM55 on 2012-07-14
It may be an issue with your video card driver. (Do you have an Nvidia video card?)
The problem may be that although you clicked and opened the drop-down menu, the focus is still in another window, so the menu system doesn't "see" the selection you want.

One thing you can try is log-off and then log-in again using the "Gnome Classic (No effects)" option. If problem not solved, go back to the regular "Gnome Classic" and see if something changed.

I had a somewhat similar that was resolved once I was able to get the Nvidia open source driver to work. The proprietary Nvidia driver was active but never kicked in (their bug) while at the same time did not let the open source driver to work either. So my video card was working in a basic mode, correct resolution but no other graphic features, no glx, no Open GL. I installed the nvidia-current driver then removed it, and suddenly everything started to work.

---

