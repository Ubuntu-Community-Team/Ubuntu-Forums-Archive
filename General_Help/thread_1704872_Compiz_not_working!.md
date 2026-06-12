---
title: "Compiz not working!"
date: 2011-03-11
forum: General Help
---

### Post by abdulqadir93 on 2011-03-11
Everything was perfect UNTIL I did some manipulations with the themes and stuff. So now ... I'm stuck here ... when I run "compiz --replace" in terminal .. I get this output:

libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

Note: I have "Intel 82G33/G31 Express Integrated Graphics Controller" which is more than capable for compiz effects. I have uninstalled emerald and re-installed compiz and ccsm. Also tried re-installing the "xserver-xorg-video-intel" entry in the synaptic package manager. All in vain.

---

### Post by lithopsian on 2011-03-11
Make sure the compizconfig-backend-gconf package is installed correctly.  That is where your missing library comes from.

---

### Post by abdulqadir93 on 2011-03-11
ok I installed "Compiz Fusion configuration system -gconf backend" from software centre ... Now there is no error occuring. But I can't enable desktop effects! When I select "Extra" from Appearence>Visual Effects" nothing happens. It reverts back to "none" immediately.

---

