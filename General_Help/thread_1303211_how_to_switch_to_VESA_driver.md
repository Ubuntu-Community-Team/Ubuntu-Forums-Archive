---
title: "how to switch to VESA driver?"
date: 2009-10-28
forum: General Help
---

### Post by baffle-boy on 2009-10-28
i had some graphical glitches in Ubuntu when i used it, but i decided that i like KDE better than GNOME. the problems i had were pretty easily fixed by switching to the vesa driver by editing the  /etc/modules and /etc/X11/xorg.conf files... i used the terminal in ubuntu to do this, but i cant use the konsole very well... and i could manually navigate to the files either... any help?

---

### Post by falconindy on 2009-10-28
The VESA driver is the default driver in X when none other are installed. Try booting without an xorg.conf at all.

---

### Post by baffle-boy on 2009-10-28
are you sure? because vesa wasn't the default in gnome, i had to manually change it to vesa, THEN it worked. so no reason it shouldn't work now... well, any other driver you could suggest that would work an a system that only has crappy integrated graphics?

---

### Post by psycho5 on 2009-10-28
Vesa is the default, or failsafe or fallback driver. That is how Ubuntu loads the desktop even without your video card's drivers. So if you don't have a config file for X, it will fallback to Vesa.

---

### Post by baffle-boy on 2009-10-28
well, can anyone please tell me how to do what i did to fix the problem in ubuntu in kubuntu? i followed these instructions:
1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"
3) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/X11/xorg.conf"
4) In Section "Device" make sure there is a line specifying the vesa driver:
Driver "vesa"


The files should end up looking similar to this:


== /etc/modules ==
fuse
lp
sisfb
== ==

== /etc/X11/xorg.conf ==
Section "Device"
Identifier "Video Device"
Driver "vesa"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Video Device"
EndSection
== == 			 		

and then it worked. the original instructions were to change driver to "sis" but only changing it to "vesa" worked. i just need to know how to do this in kubuntu. or maybe there is another driver i could try that would work?

---

### Post by baffle-boy on 2009-10-28
i'd hate to bump... but i kind of need this to be fixed... surely it isn't that hard to switch to a working driver... or maybe it was simply the changes to /etc/modules that did it, but i dont know where the equivalent file is in kubuntu.

---

### Post by spcwingo on 2009-10-28
> **baffle-boy said:**
> well, can anyone please tell me how to do what i did to fix the problem in ubuntu in kubuntu? i followed these instructions:
1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"
3) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/X11/xorg.conf"
4) In Section "Device" make sure there is a line specifying the vesa driver:
Driver "vesa"


The files should end up looking similar to this:


== /etc/modules ==
fuse
lp
sisfb
== ==

== /etc/X11/xorg.conf ==
Section "Device"
Identifier "Video Device"
Driver "vesa"
EndSection
Section "Monitor"
Identifier "Configured Monitor"
EndSection
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Video Device"
EndSection
== == 			 		

and then it worked. the original instructions were to change driver to "sis" but only changing it to "vesa" worked. i just need to know how to do this in kubuntu. or maybe there is another driver i could try that would work?

You should be able to do exactly as you listed above just replacing "gksu gedit" with "kdesudo kate".

---

### Post by baffle-boy on 2009-10-29
oooook i just replaced gedit with kate... didnt know that the command was kdesudo... thanks a lot, ill try it right now!

---

### Post by spcwingo on 2009-10-29
Did that do the trick for you?  If not, I know another method that just might do the trick.

---

### Post by Count Chocula on 2009-10-29
Thank you for this info. I have SiS 760 integrated graphics and it was working in Jaunty, but it was locking up in Karmic until I saw this thread and tried it. Now it seems stable. (The sisfb module didn't seem to matter, it behaves the same without it, as long as the vesa driver is listed in xorg.conf).

But the bad thing now for me is that it is defaulting to 60 Hz, and it used to do 75 Hz. Unfortunately 60 Hz gives me headaches within a few minutes so I still need to find out how to fix the refresh rate now that it is using the vesa driver. This is in Karmic again, so I don't know much about the autoconfig stuff versus the old xorg.conf options, what do I do nowadays? When I try the display preference panel, it lets me change the resolution, but the refresh rate is shown as 0 Hz, and is unchangeable.
:???:

---

