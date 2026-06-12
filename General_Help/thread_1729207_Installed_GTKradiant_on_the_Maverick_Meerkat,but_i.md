---
title: "Installed GTKradiant on the Maverick Meerkat,but it is nowhere to find"
date: 2011-04-14
forum: General Help
---

### Post by PCaddicted on 2011-04-14
Hi,
I have downloaded GTKradiant 1.5.0(from GameFront) in rpm format and converted it to deb using alien.I ran that deb file to install the program.After the instalation completed,I closed Ubuntu software center.
However,I cannot find GTKradiant anywhere on my system.Any idea what's the cause and how could I solve this problem?
I use Ubuntu 10.10(that's why I posted this on the Ubuntu forum;does GTKradiant have any compatibility issues with Ubuntu?anything special to say about running that softwre on the mentioned OS?).
(Note:I want to use Gtkradiant to create levels for the Neverball game). 
Help!
Yes,I've installed libgtkglext1.I've tried to run /opt/gtkradiant/radiant.x86 but I got:
"./radiant.x86: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory".
I tried to install the libgtkglext dev package but I got:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtkglext
E: Unable to locate package dev"
Then,I tried to install libgtkglext1 dev(maybe that's the correct name) and I got:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dev"
I'm starting to lose my temper.Please,give me a hand!

---

### Post by dino99 on 2011-04-16
follow this howto:

[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fgtkradiant](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fdoc.ubuntu-fr.org%2Fgtkradiant)

---

### Post by PCaddicted on 2011-04-16
I've followed the procedure described there,but I'm still experiencing that problem.If I type:
/opt/gtkradiant/radiant.x86,I will get:
"/opt/gtkradiant/radiant.x86: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory".
If I type:
/ opt/gtkradiant/radiant.x86
I will get:
"bash: /: is a directory" and nothing will happen.
I have all the required libraries(I've checked that),but this thing really aims to walk on my nerves!Any idea how to solve this problem?

---

### Post by PCaddicted on 2011-04-16
In fact,I was lacking some libraries...I have installed them but now I am getting the segmentation fault!Help,please...

---

### Post by Lucradia on 2011-04-16
What's the output of uname -a (ON THE SYSTEM THAT HAS SEGMENTATION FAULT, before you had the fault of course. Don't use liveCDs, etc. It will tell us nothing of your system that had the error.)

---

### Post by PCaddicted on 2011-04-17
Here's the uname -a output:
"Linux PCaddicted-EP31-DS3L 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux"
(my username is PCaddicted)
(Lucradia,I hope you know what is this problem we are talking about here:I have installed the GTkradiant software and the required libraries on my Ubuntu 10.10 system.When I try to run Gtkradiant,I get the segmentation fault:
 "Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

Segmentation fault").
Only the Gtkradiant program has this problem,not the system itself...
I advise you to read all the posts in this thread for better comprehension.

---

### Post by Lucradia on 2011-04-17
I was just wondering, because you may have forced a make for an x86 program on a 64-bit arch distro, which isn't the case thanks to your uname.

---

### Post by PCaddicted on 2011-04-17
So,is there anything to do about it?

---

### Post by PCaddicted on 2011-04-18
In fact,I realised I had that radiant directory.I changed the contents of the global.pref file to:

<?xml version="1.0"?>
<qpref version="1">
<epair name="gamePrompt">false</epair>
<epair name="gamefile">doom3.game</epair>
<epair name="log console">false</epair>
</qpref>

,as I heard I have to do in order to run gtkradiant.But it was absolutely useless.
Anything to do about this problem???

---

### Post by PCaddicted on 2011-06-09
bump

---

