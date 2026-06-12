---
title: "Help: VmWare in Ubuntu"
date: 2006-01-21
forum: General Help
---

### Post by spime23 on 2006-01-21
Recently i have installed vmware in my Ubuntu Desktop (PC: 2.4 GHz , P4; 256 RAM).

I want to run Windows XP Pro in Ubuntu through vmware. What will be the optimum configuration (basically i want to know RAM size of virtual Windows XP Desktop) so that i can run Windows XP easily from Ubuntu.

---

### Post by MartinG on 2006-01-21
256 RAM is a bit tight, I think, and will inevitably involve a lot of memory swapping to disk, but VMWare seems to make sensible recommendations in its setup.  I run Windows 2000 Professional, not XP, in VMWare on a machine with 512 RAM. 

The settings I use (the defaults) are as follows:
Max RAM for all virtual machines 376, RAM for W2K 176.
It also suggests minimum possible for W2K is 64, maximum advisable 276.

I'd suggest you need at least 128 to run WinXP with any degree of comfort without compromising Ubuntu.  You could maybe go up to 192 if you really squeeze Ubuntu; in particular if you use a lightweight window manager (IceWM, XFCE, etc.) rather than Gnome (or KDE).

---

### Post by VR6Pete on 2006-01-21
You will need to upgrade your memory to at least 512MB RAM to make your VM sessions run even remotely smoothly.

---

