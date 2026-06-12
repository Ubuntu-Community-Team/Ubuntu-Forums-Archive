---
title: "rc.local does nothing"
date: 2010-03-03
forum: General Help
---

### Post by methano1 on 2010-03-03
For the life of me I cannot figure out how to get /etc/rc.local to launch anything.  I even have tried putting something like touch /tmp/rcstarted, but it simply does nothing. I have been trying various files from the rcN.d directories to random scripts that I think should start for over an hour.  Nothing simply seems to work.  

It shouldn't be this complicated to start something on boot.

Thank you for any help.

---

### Post by JKyleOKC on 2010-03-03
The default copy of rc.local, in /etc, includes a line that reads "exit 0" so everything following that line will have no effect at all. If you're simply adding your commands to the end of the file, the exit will prevent them from being seen by the init programs. This might be what is happening.

In general, random editing of the "rc" files is a bit like playing Russian Roulette with an automatic pistol. The results are likely to be fatal to your system! This is especially true for the S, 0, 2, and 6 files; 3, 4, and 5 are not so likely to cause strange things to happen.

If you're getting guidance from most of the Linux books in print, or familiar with other distributions, note that Ubuntu and its kin are using a totally different initialization scheme and while runlevels still exist, they're quite different from those that most books describe!

---

### Post by spiderbatdad on 2010-03-03
been quite a while since I have had the need to run my own startup scripts, but it seems in the present file system /etc/init.d is the place for the scripts and the command update-rc.d is used to create the symbolic links necessary in /etc/rcN.d
This from the readme files in /etc/init.d & /etc/rcN.d

---

### Post by craigrose on 2010-03-03
I came to the same conclusion that rc.local does nothing or is so old school that it only still exists for legacy support and that the /etc/init.d and /etc/rcN.d folders were the place for startup and shutdown scripts.  You can see references to rc.local and local there so they may still be usable, but how?

Unable to get any joy out of rc.local et al I did this: [http://ubuntuforums.org/showthread.php?t=1420420](http://ubuntuforums.org/showthread.php?t=1420420) , but still haven't got it to work.

---

### Post by bodhi.zazen on 2010-03-03
This is a common problem. The issues stems from what is called concurrency, the boot scripts run at the same time, and rc.local often runs too soon.

You often simply need to add a sleep

sleep 10
command 1
command 2
exit 0

---

### Post by JKyleOKC on 2010-03-03
> **bodhi.zazen said:**
> You often simply need to add a sleep

sleep 10
command 1
command 2
exit 0Many thanks for this message! While I've not yet run into such a problem myself, it's nice to know what can be causing it.

---

