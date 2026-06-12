---
title: "Terminal will not start"
date: 2012-04-02
forum: General Help
---

### Post by thewalle11 on 2012-04-02
After accidentally copying libncurses.so to /usr/lib, my terminal will not start.  Synaptic package manager will not start, and I get the following error message when I try to log in through Ctrl + F1: "-bash: error while loading shared libraries: /lib/libncurses.so.5: ELF file data encoding not little-endian"

How do I fix this?  The libncurses.so was accidentally copied from a folder with libraries for an embedded linux system that I am working on, and is not specific to my ubuntu system...

---

### Post by oldos2er on 2012-04-02
You can download libncurses from packages.ubuntu.com: 
[http://packages.ubuntu.com/oneiric/libncurses5](http://packages.ubuntu.com/oneiric/libncurses5)

If you're not using oneiric you'll need to change that to whatever version you're using.

---

