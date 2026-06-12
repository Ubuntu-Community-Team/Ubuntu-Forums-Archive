---
title: "Gimp can't loading shared libraries"
date: 2009-12-26
forum: General Help
---

### Post by mr.suchy on 2009-12-26
Hi,

When I run Gimp I have this error

```
gimp: error while loading shared libraries: libbabl-0.0.so.0: cannot open shared object file: No such file or directory
```

I have this problem after update kernel from 2.6.28-15 to 2.6.28-17. I try reinstall gimp from "add/remove" but nothing happens.

Regards

--edit

```
sudo dpkg -i libbabl-0.0-0_0.0.22-1_i386.deb

```

of course download .deb from [http://packages.ubuntu.com/jaunty/i386/libbabl-0.0-0/download](http://packages.ubuntu.com/jaunty/i386/libbabl-0.0-0/download)

---

### Post by BCtom on 2010-04-11
Thank you very much! 

This probably saved me about 2 hours of running through the usual panic and roaming through the world wide web looking at endless threads of stuff that may or may not help. Your post was right to the point, and helped me out a lot. I was not aware that you could download each lib file and force it to install - I learnt something new to day.

Cheers

---

