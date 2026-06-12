---
title: "How do I get GUI to display on HDTV (CRT)?"
date: 2009-10-23
forum: General Help
---

### Post by dmanno on 2009-10-23
I am unable to get any display after Ubuntu loads (I get a Unusable Signal error on my TV). I can get to a terminal with ctl+alt+2 just fine, but I can not see the desktop. I'm running Ubuntu 9.04 with an ATI Radeon 9800 pro on a CRT HDTV.

I can see the desktop fine using an LCD monitor. 

Any ideas?

---

### Post by jbrown96 on 2009-10-23
What type of connection is being used (hdmi, component, etc.)?

---

### Post by dmanno on 2009-10-23
I'm using a DVI connection

---

### Post by jbrown96 on 2009-10-23
CRTs have different refresh rates than LCDs, so that or a resolution problem is what's occuring. You really need to consult your owner's manual (or find it on the web) before doing this. There are values for resolution/refresh rate, which can break you TV. You need to figure out what settings the TV supports and only apply those. Don't just guess and check with this!

1) switch to a terminal
2) set the resolution and refresh rate with ```
xrandr -s 1920x720 -r 50
``` obviously replace with the correct value. If that complains about privileges, just do ```
sudo !!
``` This is a cool trick. It will run the previous command with root privileges. 
3) Try switching back to the gui (ctrl+alt+f7)
If that works, the solution will not be permanent, so go into system-->preferences-->screen resolution and set it properly there. Ubuntu should now remember it.

---

### Post by dmanno on 2009-10-23
Cool, I'll give it a try when I get home. Thank you! I will say, however, that I have tried the "xrandr" command before, I believe, and I get an "Unable to open display" error. I have received that error while trying other commands. But I'll give it a try. 

And thanks for the cool tip about "sudo !!", there are times when I've wished I could do something like that!

---

### Post by jbrown96 on 2009-10-23
I know what you mean with xrandr. Since X is probably failing to start, it probably won't like changing the resolution. You can try changing the resolution in xorg.conf by inserting a modeline. There's tons of guides on how to do it.

---

### Post by dmanno on 2009-10-23
Thank you so much for your help. I'll try all of these things when I get home from work.

---

