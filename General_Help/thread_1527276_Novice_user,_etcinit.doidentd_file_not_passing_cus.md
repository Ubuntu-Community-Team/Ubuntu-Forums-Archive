---
title: "Novice user, /etc/init.d/oidentd file not passing custom options"
date: 2010-07-09
forum: General Help
---

### Post by duckdown on 2010-07-09
Hi there, novice user here, but am having a problem.

[img]http://img130.imageshack.us/img130/310/scr1278662485.jpg[/img]

I am trying to run the oidentd daemon, but I need to add the "-a 0.0.0.0 -a ::1" switches to the command line, so I edited /etc/init.d/oidentd and put "-a 0.0.0.0 -a ::1" in the OIDENTD_OPTIONS line, yet after I do a /etc/init.d/oidentd restart, the flags are still not being used when I do a ps -aux .  

What am I doing wrong?  Why aren't these flags being passed, even though I've added them?

Thanks in advance!

---

### Post by gzarkadas on 2010-07-09
Please post -inside a code block- the command line the init script uses to run the oidentd binary (or the entire init script if you can't locate it by browsing at the code).

---

