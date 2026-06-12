---
title: "Screen Screwed up (Possibly x-server)"
date: 2009-08-05
forum: General Help
---

### Post by Beezleray on 2009-08-05
Hey I need some help,
My screen visually is all messed up, everything works but the screen is all screwy, horizontal lines messing everything up. I really don't know how to describe it, it kind of looks like a corrupted image file. If you know where to click it all works fine though and on load up everything looks normal until you hit the login screen.

I've replaced my xorg.conf file with the failsafe and that did nothing, I tried to access the recovery menu but when I select it, text starts scrolling by really fast and you can see the blue and grey recovery menu for a second as it speeds by followed by more text then everything loads normally.

Any help would be greatly appreciated!

---

### Post by Beezleray on 2009-08-07
Please, anything will help.

I'd really hate to have to reinstall ubuntu and loose everything :(

---

### Post by sergioagrelo on 2009-08-07
I have the same problem...All images in my screen look terrible, they vibrate like an old tv with antenna  problems...the rest is ok...also I need help on this issue :(

---

### Post by Beezleray on 2009-08-07
Here is my xorg.conf file if that'll help:

(I'm rewritting this from the problem comp so there may be some typos)

> Section "Monitor"
Identifier "Configured Monitor"
End Section

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "nVidia"
Option "NoLogo" "true"
EndSection


Also In my Linux restricted modules common file, it showed

DISABLED_MODULES=""

So I added nv to it but nothing changed.

---

### Post by Beezleray on 2009-08-07
[IMG]http://img43.imageshack.us/img43/7608/screenshot3srd.png[/IMG]

Screenshot might help.

---

### Post by kayvortex on 2009-08-08
What video card do you have? Post the output of
```
lspci
```
if you're not sure. Press Ctrl-Alt-F1 to enter a virtual console (and Ctrl-Alt-F7 to get back to the GUI) to work on your system -- all text based, obviously.

You could try restarting gdm and see if that works:
```
sudo /etc/init.d/gdm restart
```
 
You could also try reconfiguring xorg; but, apparently, it doesn't work anymore. Still, you can give it a try. [Here]("http://ubuntuforums.org/showthread.php?t=690760")'s a link to follow.

---

