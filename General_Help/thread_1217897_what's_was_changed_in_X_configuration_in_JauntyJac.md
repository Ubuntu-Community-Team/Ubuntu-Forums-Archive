---
title: "what's was changed in X configuration in JauntyJackalope, relating to keyboard config"
date: 2009-07-20
forum: General Help
---

### Post by alfonz19 on 2009-07-20
Hi,

few years I wrote my own keyboard layout, and I have some difficulties to get it working under Jaunty. First of all I realized that config dir moved from /etc into /usr/share and after that I found that usual configuration process:

1.modify existing file containing symbols definition
2.register new layout in files xfree86.lst and  xfree86.xml

does not work anymore:
I also tried to add it into file symbols.dir

but my keyboard layout still does not get listed. So what's wrong? I'm currently using kde 4.X if it's important.

---

### Post by bobince on 2009-07-20
> **alfonz19 said:**
> 2.register new layout in files xfree86.lst and  xfree86.xml

Probably you need to add the layout to evdev.lst/.xml instead of (or as well as) xfree86. That's the only way I could get my layout to appear.

(Not sure what the difference is or why there are so many seemingly redundant keyboard config files; historical reasons maybe? This is one of those muddy areas in Linux where the documentation is largely poor, out-of-date or non-existant.)

---

