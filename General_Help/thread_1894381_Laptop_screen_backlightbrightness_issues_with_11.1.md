---
title: "Laptop screen backlight/brightness issues with 11.10"
date: 2011-12-12
forum: General Help
---

### Post by Cupcake123 on 2011-12-12
Hi,

I previously used Xubuntu 9.10 32-bit, but recently started using Lubuntu 11.10 64-bit.

I have a Lenovo 3000 N200 laptop with an Nvidia Geforce Go 7300 chip. It has 8 possible LCD backlight brightnesses; I'll refer to them as level 0 to 7 here.

With Xubuntu 9.10, I could select any brightness easily. In Lubuntu 11.10 however, while the backlight controls still work (Fn-F10 and Fn-F11 on my keyboard), each press changes the brightness by two levels, like this when increasing the brightness:
  0 -> 2 -> 4 -> 6 -> 7
and like this when decreasing:
  7 -> 5 -> 3 -> 1 -> 0

So while I can still select any possible brightness level, it's a bit of a hassle. For example, to select brightness 5 I can change the brightness to maximum (7) then press Fn-F10 to reduce it to 5. To change from 5 to 4 I'd need to reduce it to 0 then press Fn-F11 twice to increase it to 2 then 4.

This happens with both the Nouveau and Nvidia binary drivers. Has anyone else experienced a similar problem?

---

### Post by ac_d600 on 2011-12-12
I was always under the impression that the screen brightness was controlled
by the hardware and not the os, so even though Lubuntu
is showing you going up 2 levels this may be more a glitch in the way Lubuntu is
showing this information than what is really happening.

This is just my opinion, I could be wrong. ;)

---

### Post by lpc921 on 2012-01-06
I have the same problem with ubuntu 11.10 on a Lenovo T520 laptop. Is there a way to disable the hotkey? I don't need the OSD.

---

### Post by Rodney9 on 2012-01-06
Following this posting - 
[http://ubuntuforums.org/showthread.php?t=1422861](http://ubuntuforums.org/showthread.php?t=1422861)

and thanks to Domu - You can check the keyboard shortcuts already set up by looking at the output of:
Code:
grep -A 2 "<keybind" ~/.config/openbox/lubuntu-rc.xml


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by lpc921 on 2012-01-06
I removed all the parts related to backlight in the xml and it didn't work. I think the power-manager takes over the control for those keys. I tried Ubuntu, Kubuntu, Lubuntu, and Fedora. They all have the same problem. Fedora somehow has one more level of adjustment. The problem is probably lying deeper in the system...

---

