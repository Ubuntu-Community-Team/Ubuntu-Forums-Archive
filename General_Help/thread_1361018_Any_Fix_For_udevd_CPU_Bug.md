---
title: "Any Fix For udevd CPU Bug?"
date: 2009-12-21
forum: General Help
---

### Post by klausner on 2009-12-21
has anyone found a solution for udevd sucking up 99% of the CPU cycles on a system? Someone on launchpad suggested uninstalling evms, but someone else countered that evms couldn't be the problem in 9.10, which is what I'm using. Since I'm not familiar with evms, I'm reluctant to remove it.

---

### Post by lusmo on 2010-01-28
Hello, I have got the same problem. My configuration is Aus UL50, Ubuntu 9.10. udevd consuming too much performance of procesor. Please help!

---

### Post by popinet on 2010-02-04
Yes, same problem here Ubuntu 9.10 udevd eating up 60% and 16% of two CPUS on a quad-core intel system.

---

### Post by klausner on 2010-03-21
Bump!

---

### Post by no2498 on 2010-03-22
open a terminal type top and or htop
terminal will tell you how to install them
just type top or htop
they will tell you what is using it

write down what its set to
so you can set it back if you need to
this worked for me on a dell 6400 desk top
open a terminal type, gstreamer-properties click enter
click video set the plugin to, x window system (no xv)
and restart the computer

---

### Post by klausner on 2010-03-22
> **no2498 said:**
> open a terminal type top and or htop
terminal will tell you how to install them
just type top or htop
they will tell you what is using it

write down what its set to
so you can set it back if you need to
this worked for me on a dell 6400 desk top
open a terminal type, gstreamer-properties click enter
click video set the plugin to, x window system (no xv)
and restart the computer

The culprit is udevd, as stated above.

---

### Post by mame_792 on 2010-04-21
Did anyone resolved the issue? I removed the ntfs, I changed the properties in gstreamer-properties, but no efect. The udevd still eats 99% of processor time. It makes 9.10 practically unusable on UL notebook. Any help really appreciated!

---

