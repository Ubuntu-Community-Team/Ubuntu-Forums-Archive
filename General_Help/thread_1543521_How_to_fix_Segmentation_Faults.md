---
title: "How to fix Segmentation Faults"
date: 2010-08-01
forum: General Help
---

### Post by JohnHeikkila on 2010-08-01
Okay, so I know I'm not the only one who has(/d) segmentation faults with Gnome desktop programs, such as Inkscape, Synaptic, etc.
I got it fixed with just a few steps. But first open your console and execute:

*gdb /usr/bin/inkscape*
Be sure to replace inkscape with your crashing program's name.
Then when gdb is opened, write *run* and do whatever you do to make the program crash.

When the program has crashed, write *bt*.
This will return the backtrace of the crash.
Now, if the backtrace has lots of text saying */usr/lib/libxml2.so.2*, it's the libxml2 that is crashing.
Steps to fix it:

[LIST=1]
[*]*sudo kate /etc/apt/sources.list*
In stead of kate, pick your favorite text editing program if you wish.
[*]Add this line to the file:
deb [http://*ftp.de.debian.org/debian](http://*ftp.de.debian.org/debian)* sid main
Add it anywhere, say into the end.
[*]sudo apt-get install --reinstall libxml2
If it needs to download a new package (around 1500kb), select yes. Also select yes to the "install an unsigned package" question. This will update the libxml2 to 2.7.7. IF it doesn't download a new package, your Segmentation Faults weren't because of libxml2.
[/LIST]

---

### Post by JohnHeikkila on 2010-08-06
Bump so people will see this thread.

---

