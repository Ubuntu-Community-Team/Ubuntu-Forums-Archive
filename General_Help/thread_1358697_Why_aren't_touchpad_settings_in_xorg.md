---
title: "Why aren't touchpad settings in xorg"
date: 2009-12-18
forum: General Help
---

### Post by decrow06 on 2009-12-18
I recently upgraded to karmic.  Unfortunately, two finger scrolling still won't work.  I'm trying to enable it, several ways.  However, in my xorg file, it shows nothing about input devices resembling touchpads.  

Also, when I run synclient -m 300 it shows a constant value of 0 for w (width).  Is there any way to update something to fix this.  I am on a latitude d620 and I know people have gotten similar things to work on d620s.  

Thanks in advance.

---

### Post by decrow06 on 2009-12-18
ok, so i've learned why touchpad settings aren't in xorg, i think.  i believe (can anyone verify) that the settings are controlled by a different file now.  namely 

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

This is helpful, however, i still can't make my synclient see a value higher than 0 for width.  please help

---

### Post by pbrane on 2009-12-18
First find out what kind of touchpad you have.

Try running **xinput -list** in a terminal. Then you can find out what properties you can set. For instance my touchpad is called "AlpsPS/2 ALPS GlidePoint" in the xinput list. Running **xinput -list-props "AlpsPS/2 ALPS GlidePoint"** then shows me *Synaptics Two-Finger Width (246):	7*. I have not tried to configure two finger scrolling on this touchpad, but you should be able to on yours if it worked before. You can set a property by running **xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Two-Finger Width" 8 20** for instance. The '8' is the integer width (8-bits) and the 20 would be the actual width.

Run **man xinput** in a terminal for more info. HAL may be deprecated depending on which Ubuntu you are running. If you are on Karmic, look for how to set up your touchpad using udev.

---

### Post by diesch on 2009-12-18
Karmic is still using HAL for configuring X input devices.

---

### Post by aaronchall on 2009-12-22
So has anyone been able to make ALPS do a two finger scroll?

---

