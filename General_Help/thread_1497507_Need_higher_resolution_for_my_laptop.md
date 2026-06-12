---
title: "Need higher resolution for my laptop"
date: 2010-05-30
forum: General Help
---

### Post by bakegoodz on 2010-05-30
I have an older Pentium 3 Toshiba laptop that looked fine in Windows XP, and was set to 1024x768. I install Ubuntu now the desktop only uses half of the screen. The video only can be set to 800x600 or 640x480. How can I set it to 1024x768. I googled much information about changing settings in /etc/X11/xorg.conf, but it doesn't matter what I put in there, it seems to be ignored. 

What can I do?

The video is Trident Blade 3D by the way

---

### Post by davidmohammed on 2010-05-30
the answer depends on the graphics card you have and the version of ubuntu (10.04??) you have installed - 

lspci | grep VGA

for the graphics

---

### Post by davidmohammed on 2010-05-30
the answer depends on the graphics card you have and the version of ubuntu (10.04??) you have installed - 

lspci | grep VGA

for the graphics

---

### Post by davidmohammed on 2010-05-30
** deleted **

---

### Post by srcsantos on 2010-05-30
Hello []("http://ubuntuforums.org/member.php?u=97284")bakegoodz.
I don't know if you have tried this before, but here goes...
Before you start, please backup you xorg.conf.
In your xorg.conf, search for the "Screen" section and add "DefaultDepth 16". Then, if it isn't already there, add this subsection:
[INDENT]SubSection "Display"
   Viewport 0 0
   Depth 16
EndSubSection
[/INDENT]Save and reboot.
It should probably work, but i make no promises...

---

### Post by bakegoodz on 2010-06-19
I fixed by shutting down Xorg, and on the console run: "Xorg -configure" then "mv /root/xorg.conf.new /etc/X11/xorg.conf" then I changed the monitor section to this in xorg.conf. Tried the exact same thing on another Larger Toshiba laptop with a Trident Cyberblade, it worked like a charm too.

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
VertRefresh 56-61
HorizSync 31.5-49
EndSection

---

