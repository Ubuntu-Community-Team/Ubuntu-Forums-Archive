---
title: "cannot start inkscape"
date: 2009-10-11
forum: General Help
---

### Post by rmausser on 2009-10-11
Hi, suddenly I cannot start Inkscape.

I tried starting it in the terminal and no messages appear. 

In the System Monitor, Inkscape has started, but has a constant 70% CPU usage, and no GUI shows up.

I am using Ubuntu Studio 9.04. 

I tried updating from 0.46 to 0.47 with a pre-release PPA and this did not solve the problem.

Help! I love Inkscape, and want to use it. 

Thanks. 

Rob.

---

### Post by rmausser on 2009-10-13
so I have discovered that Inkscape will run if I create a new login.

So some login dependent files are causing inkscape to not run. 

Is there anything I need to/can remove in my home folder? 

Thanks. 

Rob

---

### Post by rmausser on 2009-10-13
solved, I had about 15,000 fonts in my .fonts folder....they work fine in Gimp but seem to interfere with inkscape running.

---

### Post by barretr on 2010-01-12
Thanks for the tip, rmausser. This one had me stumped. 

One possible workaround would be to create a symbolic link in /usr/share/fonts allowing for quick addition or deletion.

---

