---
title: "Basic question on gnome-terminal"
date: 2011-09-13
forum: General Help
---

### Post by GammaPoint on 2011-09-13
I recently switched to Xubuntu with xfce. However, the default terminal that pops up isn't much to my liking (couldn't figure out how to make it partially transparent). I installed gnome-terminal and that looks great. My question (and this is mostly a question of understanding and not of practical significance since gnome-terminal seems to work) is whether there is anything "wrong" or potentially problematic with running gnome-terminal when you're not running gnome? Or is gnome-terminal simply a terminal program which has the same look and functionality as the default terminal in gnome?

Thanks.

---

### Post by Habitual on 2011-09-13
gnome-terminal is the very first thing I install when I use Xfce.
Never had a problem with doing so.

---

### Post by Zeta-K on 2011-09-13
As long as you have gtk, which you do, gnome-terminal should run fine.

---

### Post by sisco311 on 2011-09-13
There are two major toolkits: GTK+ and Qt

GNOME and Xfce are based on GTK+ and KDE is based on Qt. But you can use without any issues GTK+ applications in KDE or Qt applications in GNOME or Xfce. In the past, there were some issues with the theme integration, but they are solved now.

So, to answer your question, there is nothing wrong with using gnome-terminal (it's 'just' a GTK++ app after all) in Xfce.

But, you can enable transparency in xfce4-terminal. Right click on it -> Preferences -> Appearance tab -> Background and select Transparent background.

For real transparency you have to enable compositing: Xfce Menu -> Settings -> Setting Manager -> Window Manager Tweaks -> Compositing -> and select Enable display compositing

---

### Post by GammaPoint on 2011-09-13
Thanks so much for the helpful replies. That answered my question.

---

