---
title: "How to change defoptions in Xubuntu 10.04?"
date: 2010-06-11
forum: General Help
---

### Post by logico on 2010-06-11
Hi everyone.  I'm trying to make the changes listed in post #5 [here]("http://ubuntuforums.org/showthread.php?t=167670&highlight=mobility+m4") to my Inspiron 8000:

There's no xorg.conf in Xubuntu 10.04.  But I figured out how to create one, and I edited it as suggested.  But there's no menu.lst in Xubuntu 10.04 either. That is, the file called "menu.lst" is located in 

/usr/share/doc/memtest86+/examples

and it has no "defoptions" line.  So how can I make the poster's suggested changes (i.e., do something functionally equivalent, assuming that's possible) to my newer system?  Thanks.

---

### Post by kerry_s on 2010-06-11
dude, thats from 2006!
there have been way many changes since then, i'm pretty sure those no longer work.

grub2 is done through /etc/default/grub now

xorg.conf you need to look at the man page for the driver, example: "man ati" it should tell you the options. to create a default xorg.conf, boot in to recovery mode, select root terminal & run "X -configure" then just copy that to /etc/X11/xorg.conf.

---

