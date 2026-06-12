---
title: "deb file"
date: 2011-04-05
forum: General Help
---

### Post by intransit on 2011-04-05
Hi,

1) What is a .deb file (I am assuming it is similar to batch in windows and will execute a number of functions)

2) Can I decompile it somehow to find out what it is actually doing (like opening the .bat in  notepad to see the code)

The .deb I am referring to is here:
[http://ubuntuforums.org/showthread.php?p=10110342](http://ubuntuforums.org/showthread.php?p=10110342)

"but if you try to compile the rt73-k2wrlz-3.0.3.tar.bz2 driver yourself you may encounter some kernel issues during the "make" process so i found a nice deb package that work fine with my 9.10 karmic koala kernel 2.6.31-22. It is attached, I had to tar.gz it in order to post it so just untar it (by clicking on it) and double click on the rt73-k2wrlz-source_3.0.3-2~ppa0~karmic_all.deb file to install it. It does the blacklist of the bad rt2500usb,rt73usb,... drivers that jeopardize the usb adapter detection."

---

### Post by veggen on 2011-04-05
No, .deb is not really like a .bat. A .sh is analogous to .bat, and a .deb is a package. It contains the program you want to install pre-compiled (so that you don't have to compile from sources) and it's dependencies (other packages it needs) specified, so that they can be gathered automatically. Sometimes, a .deb doesn't have any special program in it, just dependencies. These are called meta packages, and are used to install a bunch or related programs in one go.
I don't really know how to see what deb contains exactly, but I'm pretty sure it's easily doable.

---

### Post by seawolf167 on 2011-04-05
You can open the .deb files with any archive manager, then extract the contents to a new directory. From there you can take a look at the individual file contents.

---

