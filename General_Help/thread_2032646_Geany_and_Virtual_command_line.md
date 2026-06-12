---
title: "Geany and Virtual command line"
date: 2012-07-24
forum: General Help
---

### Post by oaxacamatt1 on 2012-07-24
Hi all,
I am using Geany editor and cannot figure out how to get the command line window on the bottom to show up.  I believe they call the virtual command line but I can't seem to figure it out. I looked all over the Geany website as well as here (a bit) but cannot find any info on it.

Any Suggestions,
M

---

### Post by codemaniac on 2012-07-24
> **oaxacamatt1 said:**
> Hi all,
I am using Geany editor and cannot figure out how to get the command line window on the bottom to show up.  I believe they call the virtual command line but I can't seem to figure it out. I looked all over the Geany website as well as here (a bit) but cannot find any info on it.

Any Suggestions,
M

Have not tried geany in my d2d activities .However does the below link help you ?

[http://www.geany.org/manual/current/#virtual-terminal-emulator-widget-vte](http://www.geany.org/manual/current/#virtual-terminal-emulator-widget-vte)

---

### Post by oaxacamatt1 on 2012-07-24
Yes I found that already and looked it over and the first time I didnt find what I was looking for.
But after second inspection I found it (isn't that the way) .

For the Future:
If you want the virtual command line on your Geany editor you must check a few things.
1. Check to see if you have 'libvte.so'
 a. In /usr/lib directory search for 'libvte.so'
2. If you have a higher version of libvte.so.X then you must point Geany to the correct version.  Appaerently it only looks for libvte.so
3. Goto your command line and set a link to allow Geany to find your version of libvte.so.X

Example:
# sudo ln -s /usr/lib/libvte.so.X /usr/lib/libvte.so

Where .X is your version number.

Cheers,
M

---

### Post by codemaniac on 2012-07-24
Yes the manual says so , Geany looks for the mentioned library libvte.so in order to load its virtual widget .

---

