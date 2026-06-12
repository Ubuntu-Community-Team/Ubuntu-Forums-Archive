---
title: "Problem with lucid and wifi"
date: 2010-10-13
forum: General Help
---

### Post by dolphin194 on 2010-10-13
Ok so here's the deal. I put lucid 10.04 desktop edition on my netbook last week. I have installed the propriatory (idk how to spell it) drivers for it last week and it worked fine until yesterday. The driver literally disappeared! 

I try to install the driver again, and it gives me an error saying
```
Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log
```So I went and looked at the log file, and it said

```
WARNING: /sys/module/wl/drivers does not exist, cannot rebuild wl driver
```

and it started to debug:

```
DEBUG: BroadcomWLHandler enabled (): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy:blacklisted
```

It did that about 4 times and gave up. I tried to create the folder at /sys/module/wl/drivers and it said that the file or directory could not be found. 

After that, I made a 10.10 flash disk and when I tried to boot it, it said ```
boot:
``` as if it was asking for something

What do I need to do to get my internet to work?

---

### Post by coldraven on 2010-10-13
I don't know for sure but on this laptop last weeks Kernel upgrade broke my wi-fi.

I posted this but got no answers [http://ubuntuforums.org/showthread.php?t=1591958](http://ubuntuforums.org/showthread.php?t=1591958)

So now when I boot I have to select the previous kernel and all is fine.
I think that I will try 10.10 64bit but that won't help you, sorry.

---

