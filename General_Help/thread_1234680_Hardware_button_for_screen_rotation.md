---
title: "Hardware button for screen rotation?"
date: 2009-08-08
forum: General Help
---

### Post by Legolover64 on 2009-08-08
Hey there,

I have a Gigabyte T1028. On the side of the computer is a special button which (in Windows) pulls up a little dashboard application for managing connections and screen rotation. Within Linux, I am not sure if this button registers at all to the computer, but it's worth a shot asking this question:

Because this computer is a tablet, it might be nice to use it in slate-mode. Is it difficult for me to tie the pressing of this button to the alternating of the screen between a normal widescreen, and a rotated thinner portrait display? This way, I could tap the button, and switch to a reader-style view of my screen. I'm sure X supports this, although I'm not entirely sure how to make it "smart" enough to remember which rotation it's at and which one to go to. Also, I don't know if there's a package to log keypresses or buttonpresses on the computer that could be used. I THINK this button triggers a modifier key plus the "x" key, but I could be wrong.

Thanks in advance!

---

### Post by Favux on 2009-08-08
Hi Legolover64,

You type 'xev' in a terminal and press the button.  You want to see a "key code".  You can then bind the key to rotation.  But that will partly depend on your tablet driver and whether it requires a specific rotation command(s).  It also depends some on your video card.

Depending it could be as simple as installing Grandr from Synaptic and then right clicking top panel and adding it.

To get a general idea you can look at how it's done with linuxwacom at the Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)

---

### Post by beke on 2009-09-26
Hi. I have added your idea for a SmartManager replacement to my thread, if that's ok. Comments very welcome! [http://ubuntuforums.org/showthread.php?t=1275975](http://ubuntuforums.org/showthread.php?t=1275975)

---

