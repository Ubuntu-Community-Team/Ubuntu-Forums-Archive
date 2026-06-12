---
title: "monitor crash"
date: 2010-05-23
forum: General Help
---

### Post by croccio on 2010-05-23
guys i installed ubuntu 10.04 2 weeks ago! and when i play to any games (as zaz, xmoto, super tux racer... etc..), download from ubuntu software center, my monitor crash and appera this!
[[IMG]http://img683.imageshack.us/img683/6306/moto0003.jpg[/IMG]]("http://img683.imageshack.us/i/moto0003.jpg/")
after appear white line on black background! any way to solve this??? on windows i haven't this!

---

### Post by croccio on 2010-05-23
can somebody help me?

---

### Post by themusicalduck on 2010-05-23
It looks like the x server is crashing for some reason. What video card do you have and have you installed any drivers for it?

First try pressing ctrl+alt+f7 to see if anything appears. If not, then press ctrl+alt+f1 and login. Then type ```
sudo service gdm restart
``` and hit enter, which should at least take you back to your dekstop

---

### Post by croccio on 2010-05-23
if i press ctrl+alt+f1 or f7 it doesn't work! apper black screen with white horizontal line!

---

### Post by themusicalduck on 2010-05-23
Next time it crashes, don't press either of those combinations. I just suggested it to see if you could find anything useful, since ctrl+alt+f7 is used to display your desktop.

Just use the command ```
sudo service gdm restart
``` to get back to your desktop. Or ```
sudo reboot now
``` to restart. This saves you hard resetting the computer at least.

For your problem, we need to know what your graphics card is and whether you installed drivers for it or not.

Type ```
lspci | grep VGA
``` in a terminal (Applications > Accessories > Terminal) to find out the graphics card.

---

### Post by croccio on 2010-05-23
i write

lspci | grep VGA
and i've this
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

---

### Post by themusicalduck on 2010-05-23
It seems like 10.04 has problems with that graphics card. Here is a page on potential workarounds - [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I also read in places that disabling the screensaver can help.

Otherwise, downgrading to 9.10 may be an option to try.

This is the bug report on the issue - [https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492](https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492)

---

### Post by croccio on 2010-05-24
i've this proble with 9.10 too!

---

