---
title: "Huge kern.log files"
date: 2009-10-06
forum: General Help
---

### Post by geoffrussell on 2009-10-06
I've got 700+ Mb kern.log files and have seen a number of other
people on the forum have been troubled by these. In my case the
problem seems to be excessive info messages coming from
the usb-storage routines. When I connect a usb-drive and write, the
kern.log file grows huge with a zillion status messages. They
don't appear to be errors, just info. 

I'd like to turn them off. I have plenty of disk, so they
are an annoyance rather than a problem, but other people might
benefit from knowing how to turn them off ... if possible.

Many thanks.

---

### Post by dino99 on 2009-10-06
maybe logrotate can help. those 700mb are filled on a single day ? how long is the history ? 
an other way: customize .bashrc

---

### Post by geoffrussell on 2009-10-07
Plug in the USB drive, start my backup (using dump) and
watch the kern log grow ... faster than bamboo in the tropics.
They aren't a problem for me ... except when logrotate starts
to gzip them and chews 99% of the CPU, but I'd like to
stop the usb info logging. A 40 Gb dump produces about a 300Mb 
kern.log file.

---

