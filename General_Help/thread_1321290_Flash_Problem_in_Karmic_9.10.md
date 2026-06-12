---
title: "Flash Problem in Karmic 9.10"
date: 2009-11-09
forum: General Help
---

### Post by Incubus9 on 2009-11-09
I'll start by citing the information, as it is not my own.  

Script courtesy of Edward Coffey

I'm just helping to spread the the info (kind of like in the movie Independence Day when they figured out how to destroy the alien ships). Anyways here's a little step-by-step.

1) Right-click your desktop, Create Document. (Don't worry about the name for now.) 
2) Copy and Paste this into the document:

#!/bin/sh
GDK_NATIVE_WINDOWS=true /usr/lib/nspluginwrapper/i386/linux/npviewer.bin.real $*

3) Save and exit this document. Rename it npviewer.bin

4) Copy-paste the following into a terminal to back-up your old file (the one we will be replacing).

sudo mv /usr/lib/nspluginwrapper/i386/linux/npviewer.bin /usr/lib/nspluginwrapper/i386/linux/npviewer.bin.real

5) Copy-paste the following into a terminal to move the patch into place.

sudo mv ~/Desktop/npviewer.bin /usr/lib/nspluginwrapper/i386/linux/npviewer.bin

6) Close Firefox and re-open

---

### Post by cantspel on 2009-11-10
this fixed it for me so far .... but now everytime i do someting with my system (update changes w/e) hes loading flash-installer twice everytime with this problem :

nspluginwrapper: no appropriate viewer found for usr/lib/flashplugin-installer/libflashplayer.so

thats hilarious annoying because of low bandwidth.

[COLOR=Red]**edit**[/COLOR]: aah i guess this was for 32arch?  well i tryed the alpha version for 64 and removed the normal flashplayer and it worked fine.

---

### Post by Incubus9 on 2009-11-10
Those instructions are actually for a 64-bit system, although I'm not saying it wouldn't work for 32, I just don't know. I haven't experienced any problems yet, but I do remember reading something about removing a repository because it installs 32 rather than the 64 bit of Adobe Flash. 

I expect there to be a more official fix soon, but I was desperately not wanting to boot into 7 just to watch hulu.

---

