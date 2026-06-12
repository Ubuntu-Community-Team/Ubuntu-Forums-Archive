---
title: "Discspan not working"
date: 2010-04-05
forum: General Help
---

### Post by cforput on 2010-04-05
I am trying to run discspan but it is not working. Here is the output when I try it:

***************************************************
Number of dvd's required to burn: 1

Sanity Check

Total files in directory 1116
Total files in all discs:  1116

Ready to burn disc 1/1.  Press Enter
Running command : growisofs -Z /dev/sr0 -speed= -use-the-force-luke=notray -use-the-force-luke=tty  -gui -V DiscSpanData -A DiscSpan -p Unknown -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/tmphraZL4.discspanlist
-speed=0.0: insane speed factor.
There was an error running growisofs -Z /dev/sr0 -speed= -use-the-force-luke=notray -use-the-force-luke=tty  -gui -V DiscSpanData -A DiscSpan -p Unknown -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/tmphraZL4.discspanlist.
****************************************************
I notice a couple of things but I don't know how to fix them. First, I put in a 4.7GB DVD but discspan reports it is 8.73999999929. Second thing I see is that it says my speed factor is insane!

Anyone have any ideas?

---

### Post by cforput on 2010-04-09
Bump

---

