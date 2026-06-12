---
title: "VIA VT 7205 on board graphics"
date: 2006-03-23
forum: General Help
---

### Post by jethro10 on 2006-03-23
Hi, 
I just bought an eSYS base unit with Suse 9.3 pre-installed, worked fine. Last night I tried Ubuntu 5.1, Gnome and it failed to find the graphics card properly.
When I logged on, the screen was all wobbly, like the wrong sync settings.
I managed to see thru this enough to see the screen resolution was set to 640x480 but the desktop seemed bigger with bits missing below the bottom of the screen. THere was no other options in the scree nsettings so I assume it was a default mode gone wrong. I also tried two different monitors, one LCD, one CRT.
It was so difficult to see the screen I gave up.
Any ideas anyone? I would like to stick with Ubuntu if possible.
Is Ubuntu 6 likely to be better at H/W detection when it arrives ?

thanks
Jeff

---

### Post by dermotti on 2006-03-23
you could try

**sudo dpkg-reconfigure xserver-xorg**

select **vesa** as your driver.

and restart x (or reboot) when r done.

---

### Post by jethro10 on 2006-03-23
Wow thats quick! ,
The trouble is the screen is so difficult to read with it 'vibrating'.

Is there a way to do this by booting into a non graphical environment?
If so, how would I do this?

Thanks

Jeff

---

### Post by dermotti on 2006-03-23
once yer booted in,  try pressing cntl + alt + F3

---

### Post by jethro10 on 2006-03-23
Your too quick answering these.......

thanks

this linux thing can be so exciting yet frustrating at the same time.

Jeff

---

### Post by justleen on 2006-03-23
[QUOTE=jethro10]Your too quick answering these.......

thanks

this linux thing can be so exciting yet frustrating at the same time.

Jeff[/QUOTE]

LoL

Almost like sex with a complete stranger hey? :mrgreen:

---

