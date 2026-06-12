---
title: "Accent keys on keyboard not working"
date: 2012-08-04
forum: General Help
---

### Post by rdh61 on 2012-08-04
Hi,

I have recently installed Lubuntu 12.04 on a laptop with a Spanish keyboard layout. This has keys to make accents on top of accented letters (see attached image). However, these keys do not work.

These keys work on the same laptop on Ubuntu 10.10 (also installed), and they also work on another (desktop) computer running Lubuntu 12.04.

I have installed language support for Spanish.

Any ideas on how I can solve this issue gratefully received.

Many thanks.

---

### Post by claracc on 2012-08-04
Run language support in preferences of main menu and make sure you have all disponible language support installed, if no install the missed ones.

What do you have in lxkeymap? I have España and current keymap: es
In this window you can test your keyboard when performing changes in it, perhaps selecting something in the right part of the window will do these keys work.

---

### Post by rdh61 on 2012-08-05
Thanks for the reply Claracc, but I have already run language support and installed Spanish, English and Italian, the three languages I use. In lxkeymap I have "Spain" and current keymap is "es".
Even so, my accent keys do not work.

---

### Post by claracc on 2012-08-05
It is a weird thing.

I suggest in lxkeymap window in the right part you can try to select spanish (including dead accent) and type in the line to test the keyboard, select each of the posibilities of spanish (dvorak, eliminate dead keys, ...) and try if any of them allows to use the accent keys.

---

### Post by rdh61 on 2012-08-05
Tried that. No result. Thanks anyway. I note on Google that others have had trouble with dead keys on Lubuntu. Haven't seen a solution yet.

---

### Post by claracc on 2012-08-05
Perhaps this thread can help you although is for lubuntu 10.04: [http://forum.lxde.org/viewtopic.php?f=8&t=1721&p=4950#p4950](http://forum.lxde.org/viewtopic.php?f=8&t=1721&p=4950#p4950)

---

### Post by rdh61 on 2012-08-06
Thanks so much claracc, that link helped me to solve the problem. The only bit that was actually essential was the last line of code, the one added to /etc/xdg/lxsession/Lubuntu/autostart. I modified the code given, in order for it to work with a standard Spanish keyboard (no variants), on my model of computer, and to use the caps key for the compose option (not really necessary):

setxkbmap -model acer_laptop -layout es -option compose:caps

Then reboot.

The codes for the various languages, models, layouts, variants and options are listed if you go to:

Preferences > Lxkeymap > Variant > Show all

---

### Post by claracc on 2012-08-06
You are very welcome.

Glad you get fixed your problem.

---

