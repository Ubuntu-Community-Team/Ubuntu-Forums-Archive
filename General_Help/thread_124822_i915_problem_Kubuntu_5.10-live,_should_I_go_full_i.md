---
title: "i915 problem Kubuntu 5.10-live, should I go full install?"
date: 2006-02-02
forum: General Help
---

### Post by hyperpsyched on 2006-02-02
oh boy...

First off let me say I really want to get Kubuntu 5.10 installed so baaaad (I can almost taste that lovely kubuntiness) but oh boy... 

I am running a Toshiba M60 laptop, 17 " widesreen (want 1200 X 800 res) with (gulp) the i915 chipset, meaning the intel gma 900 graphics acclerator. Well both ubuntu 5.10 and kubuntu 5.10 live cds are not working... and I am a little nervous going ahead with a full install without at least understanding why i am having problems. So here is as complete an explanation as I can provide.

I boot both cds and all seems well and good until the X server starts up. In ubuntu this causes this bluish error message to pop up and the output thereafter becomes pretty tough to read. In Kubuntu it just hoes to the command prompt. Either way both end up at the prompt. so I try start X and on both flavours and I get this:

***********

skipping "/usr/X11R6/lib/modules/libGcore.a: m_debug_clip.o" No Symbols Found
... 
(same for m_debug_norm.o and m_debug_norm.o)
...

(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No video BIOS modes for chosen depth
(EE) Screen(s) found, but none have a usable configeration
 Fatal Server Error: No Screens Found (ouchhhhhh!)
...blah, blah
 XIO: fatal IO request 104 (Connection reset by peer) on V server "0:0" after 0 requests (0 known processed) with 0 events remaining


*************

Ok... that sucked a little bit.

I took a look at ny xorg.0.log file (seems to be the thing to do :)

****
..blah
(==) ServerLayout "Default Layout"
(**) |--> Screen "Default Screen" (0)
(**) |   |--> Monitor "Generic Monitor"
(**) |   |--> Device "Intel Corporation Default Card"
(**) |--> InputDevice "Generic Keyboard"
(**)           "                 "Configured Mouse"
(**)           "                 "Synaptics Touchpad"
(WW) the directory "/usr/share/X11/fonts/Cyrillic" does not exist. Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.

***

Ok... greek to me so then I checked out my org.conf file and all I found were directory locations for fonts... nothing else. Nothing mentioning any other type of hardware at all. Boo.

I typed in "man /etc/X11/org.conf" and everything, including the font locations was there, or so it seems. Any way it looks like this:

*****

Section "Module"
     Load "GLove" // is this right? where is the special sauce :)
     ...
Endsection

Section "input Device"
     Identifier "Configured Mouse"
     ...
Endsection

...some other sections for Keyboard, Synaptics Touchpad, etc...

Section "Device"
     Identifier "Intel Corporation Intel Default Card"
     Driver "i810" //is this the problem? I have the i915
     BusID   "PCI:0:2:0)
EndSection

Section "Montor"
     Indentifier "Generic Monitor"
     option "DPMS"
Endsection

Section "Screen"
     Identifier "Default Screen"
     Device "Intel Corporation Intel Default Card"
     Monitor "Generic Monitor" Default Depth 16
.... wole bunch of ,Subsection "Display", here all with Modes "1440 x 900" and Depth values of 1 4 8 15 16 and 24.

Section "ServerLayout"
  ... all the stuff above in here.
Endsection

Section "DRI"
     mode 0666 //this must be the problem, he devil's number! :)
Endsection

****

Should this file not be in my xorg.conf file?

So this is all I have. I have seen some forums for other linux distros with i915 probs and the fixes sound cryptic. What I need is a clear explanation of the problem and a pretty coherent answer to this question. Is it worth the hassle of installing Kubuntu 5.10 onto my harddrive as dual boot? Or am I stuck with XP, cry :( If I should go with the install what do I need and how do I install it? How easy are these fixes for a brave, if somewhat computer illiterate, newbie. I will try anything though as I figure if it messes up I can simply format the partition Linux is on an trytry again.

Please help me, I need Linux... I am already using Cygwin more than Windows and colinux nearly gave me an aneurism while trying to install.

Thanks from Hyperpsyched

---

### Post by mlomker on 2006-02-02
You could always use VESA to get a desktop if you install to hard disk.  Breezy will use the i810 driver for your card.  There are a number of threads regarding the 915resolution and 855resolution tools that you have to use to set your video mode.  [Look here.]("http://www.ubuntuforums.org/showthread.php?p=480716#post480716")

---

