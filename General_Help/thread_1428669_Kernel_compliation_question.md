---
title: "Kernel compliation question"
date: 2010-03-13
forum: General Help
---

### Post by blazemore on 2010-03-13
Hi all, I'm interested in compiling a more recent kernel, one that's heavily optimised for my specific hardware.
At the make xconfig stage, how should I know what to load and what to leave out, in terms of device drivers and other features?
Are there any online resources that can help me with this?

---

### Post by jfparis on 2010-03-13
First if you go to /boot

There will be a config-2.6.XXXXXX file. You need to copy this file to your kernel tree. It need to be renamed .config (don't forget the leading ".") That will give you the current Ubuntu kernel configuration as a starting point.

Then in order to know what modules are currently loaded on your machine you can use

```
lsmod
```It is very likely that the modules that are currently loaded will be required (either built in or as module). However it does not mean that will be sufficient. 

You will have to search for every item of hardware that you are currently using.

Good luck

---

