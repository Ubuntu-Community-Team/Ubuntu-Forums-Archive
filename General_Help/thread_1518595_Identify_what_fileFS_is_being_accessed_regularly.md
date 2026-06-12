---
title: "Identify what file/FS is being accessed regularly"
date: 2010-06-26
forum: General Help
---

### Post by coyoteboy on 2010-06-26
I'm trying to do some power saving on my system which spends lots of time idle, so I'm trying to cache most stuff to RAM but some process, I'm not sure which, is accessing /dev/sda about once a second. The other two drives will happily spin down but this one won't. This may be because one of the services needs to repeatedly access it, but it may be a stray useless process I can kill off so it would be nice to identify it. I've tried lsof to list all files being accessed but I've not identified how to make use of this info to identify the regularly-accessed file - can anyone waffle around this for me to make it a little clearer?

Cheers

---

### Post by gzarkadas on 2010-06-26
You can use `powertop' to find the top consumers of power in your system. This may also help you to spot the process in question.

---

### Post by coyoteboy on 2010-06-28
Thats a fair point, I suppose the intermittent blips may average high over time. Cheers.

---

