---
title: "black screen on boot"
date: 2010-05-07
forum: General Help
---

### Post by Nr90 on 2010-05-07
Hi guys,
Let me start off by saying that I know very little about ubuntu and linux.
I've been using 9.10 for about a year now, however just for browsing the web and typing a text etc.
So I know very little about the terminal etc.
Ok about my problem. I've got an old dell inspiron 510m (so with intel 855 chipset).

I used to use 9.10 without problems. Recently I upgraded to 10.4 and when booting I get the black screen that more people have experienced. After the dell screen I get some flashing text (used to be just a underscore bar flashing, changed with all the things I tried). Then it goes to blank without any activity.
It will boot when I select the oldest kernel in grub and run in failsafe graphic mode.

I tried searching the forum and tried solutions that other people used. However this did not work for me (could very well be due to my limited knowledge).
I'm downloading the text based installer to give a clean install a try.

Any ideas on things to try to get my laptop working again?

---

### Post by jbrown96 on 2010-05-07
When you boot press escape of shift to get the grub menu where you can select the kernel. Choose the newest one that is marked "recovery". it's probably the second entry. That will give you a text-based menu that has something about "fix Xorg" or something like that. Select and let it do it's thing.

If you have a normal US keyboard (your multimedia keys and stuff don't matter), then you will be able to press "enter" through all the menus and accept the defaults.

---

### Post by jaasland on 2010-05-07
I experienced the same blank screen problem. This fix (solution 1) worked for me:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

Jarle

---

### Post by Catharsis on 2010-05-07
Do the old kernels get you to a normal desktop (without recovery mode, low-graphics mods, etc)?

The issue with Intel graphics seems to have been introduced with the 2.6.32-21 kernel, so the previous ones should still be fine if the issue is in fact the intel driver.

If the Intel driver *is* the problem, you can check here for some things to try:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Of course, it could also be a million other things.

---

### Post by Nr90 on 2010-05-07
Jbrown thanks for the tip, but didn't work :(
I tried choosing DPKG (or something) which says recover or repair broken packages.
That results in a message saying no packages are installed/upgraded/repaired.

I'll have a look at that one jaasland

From the 3 kernels I can choose all get me the black screen unless I choose the oldest one and run with the low graphic mode.
It does the same when running the installer from USB or CD as well. Even when I add modeset.i915=0
Will read that page Catharsis, thank you!

---

### Post by Nr90 on 2010-05-07
> **Catharsis said:**
> Do the old kernels get you to a normal desktop (without recovery mode, low-graphics mods, etc)?

The issue with Intel graphics seems to have been introduced with the 2.6.32-21 kernel, so the previous ones should still be fine if the issue is in fact the intel driver.

If the Intel driver *is* the problem, you can check here for some things to try:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Of course, it could also be a million other things.

Thank you!
Changing the modeset to 1 did the trick for me! I was changing it to 0 everywhere >.<

---

