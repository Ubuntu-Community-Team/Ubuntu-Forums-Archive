---
title: "Alsamixer transparency (how I did it)"
date: 2010-12-22
forum: General Help
---

### Post by djeikyb on 2010-12-22
I wanted alsamixer to support transparency. Took a bit of googling and a wee bit of hacking, but nothing too hard. This guide probably relevant only to alsa-utils 1.0.21+.

**Know your system**
Make sure libncurses (development version with headers etc) is installed.

Run *cat /proc/asound/version*. This will tell you your alsa-utils version.

**The dirty work**
Download the source for your version of alsa-utils.[https://launchpad.net/ubuntu/+source/alsa-utils](https://launchpad.net/ubuntu/+source/alsa-utils)

Extract it, go into *alsa-utils*/alsamixer/*. Edit colors.c. Look for the section *void init_colors(int use_color)*. For each line that starts with *init_pair(* and has *COLOR_BLACK* as the second colour, change *COLOR_BLACK* to *-1*. Eg:
```
init_pair(1, COLOR_CYAN, COLOR_BLACK);
```becomes```
init_pair(1, COLOR_CYAN, -1);
```

Save *colors.c*. Run *make*. Copy the resulting *alsamixer* to */usr/local/bin*.

**Sources**
[https://www.prof-maad.org/blog/2009/11/11/transparent-alsamixer/](https://www.prof-maad.org/blog/2009/11/11/transparent-alsamixer/)
[https://bbs.archlinux.org/viewtopic.php?id=92518](https://bbs.archlinux.org/viewtopic.php?id=92518)

---

