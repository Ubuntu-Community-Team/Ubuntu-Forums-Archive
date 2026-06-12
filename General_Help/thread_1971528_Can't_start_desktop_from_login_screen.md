---
title: "Can't start desktop from login screen"
date: 2012-05-02
forum: General Help
---

### Post by electrojustin on 2012-05-02
I just recently upgraded from 11.10 to 12.04 with little to no trouble (some minor difficulties with the new kernel and my graphics driver). Now, an Xorg update comes through the tubes and suddenly I get black screens when trying to boot normally.
 I still had a custom grub entry for 3.0.17 command line, so I boot into it and reinstall xubuntu-desktop, my graphics driver (fglrx), xserver, xfce4, and lightdm and am able to get to the login screen, but when I try to log in I get some quick, flashing kernel messages and I'm put back on the login screen.
 Upon further investigation, I am able to boot into my desktop using "startxfce4", though without audio and a really wonky permissions system. I set lightdm to disable on runlevel 3 and wrote the custom grub entry to boot 3.0.17 to runlevel 3. "Telinit 2" results in a glitchy login screen that does the same thing as described above. At the moment, lightdm is not running, so I suspect that may be part of the problem. Any ideas?

---

### Post by electrojustin on 2012-05-02
@Minyfrieree
Reported as abuse

Update: gdm works quite fine thought I do not consider this a permanent fix.

---

### Post by electrojustin on 2012-05-02
Ok it seems it's a problem with my custom lightdm wallpaper...anyone figure out how to fix that?

---

