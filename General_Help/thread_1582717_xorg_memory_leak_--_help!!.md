---
title: "xorg memory leak -- help!!"
date: 2010-09-26
forum: General Help
---

### Post by nerdy_kid on 2010-09-26
So this has been going on for a long long time and has finally gotten to the point that I can't stand it any longer.  Xorg routinely is using around 400Mbs of ram (usually more) at the end of a day.  That is absurd.  I have NVIDIA geforce 8600M with the 260.19.06 drivers.  Running KDE 4.5.1 on 2.6.32-24-generic with xorg-server 2:1.7.6-2ubuntu7.3. GLX version: 1.4 by NVIDIA.  Only 72159K (72mb) of that memory is being used for pixmaps (so says xrestop).  I had heard some rumors that chrome and flash cause x memory leaks so; I am running (and always have open) Google Chrome 6.0.472.63 with Flash 10.1.85.3.  I can not reproduce the leak.

Help!

---

### Post by harrismh777 on 2010-09-26
First, if you believe that there is a memory leak in xorg you will want to file a bug report with that group. 

As for whether the 400m mem usage is absurd, well, that depends on philosophy and opinion; through in a dash of personal preference, and season with attitude. Who determines what is absurd memory usage?

My machine has been running for about an hour tonight and top shows my xorg memory usage as 400m...  about 2.8 % of memory. Now, I must admit that over time X on linux has become somewhat bloated... but not nearly as bloated as the windows gui which can eat up half of available memory. So, this is a relativistic discussion. 

Again, if you notice that memory usage is increasing "abnormally" over time and you believe you have a memory leak, you're going to need to do a little diagnosis (close things down until the leak goes away) and try to isolate the component that has the leak; then file a bug report.

:popcorn:   Hope this helps some.

---

### Post by nerdy_kid on 2010-09-27
thanks for the tips :)

about the memory footprint:  I have a lucid machine running GNOME under an ATI card that has been running for *days* and the whole system uses less then 400mb!  Xorg using 17mb of memory.  I think that X using 400mb is totally just wrong; unless it has some type of memory adjustment mechanism in it -- xorg using memory according to how much free ram is available.  (the ati machine has 1gb of ram the nvidia one has 3gb)

---

