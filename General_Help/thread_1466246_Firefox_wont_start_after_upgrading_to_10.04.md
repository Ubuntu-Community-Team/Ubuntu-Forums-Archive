---
title: "Firefox wont start after upgrading to 10.04"
date: 2010-04-30
forum: General Help
---

### Post by stephanecharette on 2010-04-30
Firefox didn't want to start after I upgraded to 10.04.

Finally, I found if I tried to start it from the command-line, it would seg fault:

[INDENT]LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/flashplugin-alternative.so [/usr/lib/firefox-addons/plugins/flashplugin-alternative.so: wrong ELF class: ELFCLASS32]
*** NSPlugin Viewer  *** ERROR: /usr/lib/flashplugin-nonfree/libflashplayer.so: cannot open shared object file: No such file or directory
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Attempting to load the system libmoon 
Segmentation fault[/INDENT]

I tried using synaptic to remove the nonfree flash plugin, but that didn't help.  Even after removing it, some files were still left, and those were dated 2007 and 2008.  I manually deleted them:

[INDENT]cd /usr/lib/firefox-addons/plugins/
sudo rm flashplugin-alternative.so npwrapper.libflashplayer.so
cd /usr/lib/mozilla/plugins/
sudo rm libflashplayer.so
[/INDENT]

That got me to the next segfault issue:

[INDENT]Attempting to load the system libmoon 
Segmentation fault
[/INDENT]
 
This one was easier to fix, as using synaptic to completely remove the libmoon package (and associated browser plugins) did fix the problem completely.  Now Firefox works for me on Ubuntu 10.04.

---

### Post by lovinglinux on 2010-04-30
Thanks for sharing. I think the problem is indeed because of libmoon, so you can try to install flash again. I would recommend the 64 bit beta version, since it seems you are on a 64bit system.

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by aftabnaveed on 2010-04-30
Thanks, deleting libmoon using synaptic helped, don't need to remove flash plugin.

thanks

---

### Post by sixshot on 2010-04-30
definitely "libmoon" package.
use synaptic to locate and "Mark for Removal"

---

### Post by Timokl on 2010-05-02
Thank you!

I had the same problem and removing libmoon solved it.

Timo

---

### Post by DonL on 2010-05-02
Thanks a lot! Worked for me as well.

---

### Post by dino99 on 2010-05-02
then clean the system:

install gconf-cleaner and use it (yes to all )

sudo dpkg --configure -a
sudo apt-get install -f

you may want to install bleachbit also, powerfull but set your settings with attention

---

