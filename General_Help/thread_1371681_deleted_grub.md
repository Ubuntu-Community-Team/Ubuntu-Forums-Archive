---
title: "deleted grub"
date: 2010-01-03
forum: General Help
---

### Post by Thistlelu on 2010-01-03
I searched for solution but couldn't find a good one

long story but i lost my grub file and now when i start my computer it doesn't load a grub and I get a screen that says something like

Grub-->

basically a command line grub.
can i fix my grub with a live cd? or by using commands from this line?

---

### Post by Brandon Williams on 2010-01-03
[Here](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode) is a bunch of useful information about how to boot into your installed system from the Grub command prompt. [This post](http://ubuntuforums.org/showthread.php?t=1195275) has a section titled 'Booting from the Rescue Mode' that gives a brief runthrough without as much detail as the first link.

Once you have used the information in those sources to boot into your installed system, run 'sudo update-grub' to rebuild your grub.cfg file. Hopefully that will get you back to a bootable if state.

If any of the above doesn't work, let us know and we can offer more help.

---

