---
title: "Removing Ubuntu from boot menu"
date: 2009-09-23
forum: General Help
---

### Post by ucal on 2009-09-23
I tried ubuntu out on my new computer to see if it would have less wireless issues than my old one had, sadly, to no avail. I made the mistake of asking it to help me to boot into ubuntu at the beginning (I didn't have a cd at the time, just the image), and now I would like to remove the choice of booting into ubuntu at start up, as I never actually installed it.  How would I go about doing that?

---

### Post by molavec on 2009-09-23
I don't understand well. Do you want to remove the Grub (the menu that appears at beginng, installed by ubuntu)? Do you have windows installed too and you want remove ubuntu and need windows starts without appears the grub options at boot? If this is your case, you must consider some things:

1.- Your disk current have 2 (or 3, considering the swap) partitions, so you must format in NTFS that ones to make visible for windows this partitions. You can use a cd ubuntu CD with GParted (the best way) or windows CD with install options for do that.

2.- probably after that step, the grub menu show you start whit ubuntu option but don't work, don't worry it is expected.

3.-Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password. (I put only enter and works for me)
In console enter the command: "FIXMBR" or "FIXBOOT"(without the quotes, i dont remember which one) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.
Note: Sometimes appear a Warning!! this is beacuse you will not can start other Operative System and with this only boots the windows, but this is what you want.
Note 2: Just I described this step how i remember that I do it when I remove a linux from a PC, so look for "Fix MBR in Windows" in google or some like this to make boot with windows boot system.

I hope that it helps you.

---

### Post by ucal on 2009-09-23
I figured it out.  The tool on the Wubi cd can be used, to remove installations, though in a roundabout manner.

---

