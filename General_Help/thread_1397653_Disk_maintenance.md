---
title: "Disk maintenance?"
date: 2010-02-03
forum: General Help
---

### Post by weirdbeardmt on 2010-02-03
Hi

Bit of a Ubuntu newbie so please bear with me. I have I have command-line 9.04 system running which runs three different webcams. It all works fine and it's streaming out over the web, no worries.

My concern is disk usage. The HDD in the machine is 20gb so not huge amounts of space. The webcam software (Motion) creates a single .jpg for each frame of the image stream it is serving. For three webcams at a framerate of 10 ps this is quite a lot of images! I've set up cron jobs to delete them at semi-regular intervals, but I'm concerned about what effect so much disk-write might have on the disk. 

This is the second time I've installed this machine as a different (160gb) HDD mysteriously died... and I'm not sure if the two are linked, or if it was just an old/bad HDD.

So is there anything I can be doing to try and keep the HDD in reasonable shape? I've installed discus to keep an eye on the usage etc.

Thanks!

---

### Post by mörgæs on 2010-02-04
If you are worried about fragmenting: Just be sure that there is always at least 20 % free space. Ubuntu takes care of the rest.

[http://www.whylinuxisbetter.net/items/defragment/](http://www.whylinuxisbetter.net/items/defragment/)
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

