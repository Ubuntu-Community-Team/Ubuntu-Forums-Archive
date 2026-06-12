---
title: "How do I theme grub2?"
date: 2011-08-04
forum: General Help
---

### Post by cjack2964 on 2011-08-04
Hi everyone, after a long night I managed to place my grub2 files on a separate partition on my hard disk.  I am now able to edit my grub.cfg file directly (no more pesky updat-grub commands :D) and I can create my own custom named menuentries in grub.cfg, the only problem I have encountered is in theming.

I originally used burg to theme my menu, but found it to be a little unstable and eratic, so I have decided to use native theming options like font, color, and splash image, but unfortuantely, all the instructions for using these features invoke editing the 05 Debian script to make changes.

As I no longer use this feature, I need to understand how editing the Debian script affects the grub.cfg file so I can manually create my menu.  If you have themed your grub2 menu, please post the contents of your grub.cfg so I can get a feel for the what commands exist.  If you have time to highlight the pertinent areas I will appreciate it, but if not I will find my way around it.

---

### Post by xdominex on 2011-08-04
Have you tried Grub Customizer?
```

sudo apt-get install grub-customizer

```

When you open grub customizer and push the "preferences" button, there is a tab for "appearance" that has some of the options you are looking for. Hope this helps!

With regards,
XSpiritusX

---

### Post by cjack2964 on 2011-08-04
i would love to do that, but because i installed grub on the seperate partition, i cant use any apps for grub.  i need to do a straight manual theme.

---

### Post by cjack2964 on 2011-08-05
I have reposted this question to make it more clear

---

