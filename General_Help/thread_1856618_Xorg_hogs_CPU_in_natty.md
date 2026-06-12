---
title: "Xorg hogs CPU in natty"
date: 2011-10-08
forum: General Help
---

### Post by Bunny Boy on 2011-10-08
Unable to pin down what is causing Xorg to use so much CPU.  When I run top it is often >50%.  Sometimes system monitor shows CPU pegged (100%) and of course at that point everything grinds to a halt.  

I thought at first that firefox was the culprit, but this has even happened immediately after login with no browsers running. 

I already checked on the wiki about this, and found that glxinfo does indeed return "software rasterizer" but they don't say what can be done about this. 

I haven't found any "infinite loop" error messages either. 

Any suggestions?

==================================
release = 11.04  
kernel = 2.6.38-11-generic
gnome = 2.32.1

RAM = 937.9 MiB
processor = intel celeron 2.53 GHz
video = ATI Technologies Inc Rage 128 Pro Ultra TR

---

### Post by claracc on 2011-10-09
Perhaps you have to install a privative driver for your ati graphics card.

You can take a look to this thread: [http://ubuntuforums.org/showthread.php?t=1724308](http://ubuntuforums.org/showthread.php?t=1724308)

---

### Post by raja.genupula on 2011-10-09
aah posted the wrong one ,sorry 

[http://ubuntuforums.org/showthread.php?t=1746327](http://ubuntuforums.org/showthread.php?t=1746327)


[http://ubuntuforums.org/showthread.php?t=1745449](http://ubuntuforums.org/showthread.php?t=1745449)

---

### Post by claracc on 2011-10-09
> 
1)sudo add-apt-repository ppa:do-core/ppa

2)sudo apt-get update

3)sudo apt-get upgrade 

Why do the poster need to install gnome-do to solve his problem?

---

