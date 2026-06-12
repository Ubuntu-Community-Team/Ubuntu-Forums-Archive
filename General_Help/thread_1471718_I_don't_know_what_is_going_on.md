---
title: "I don't know what is going on"
date: 2010-05-03
forum: General Help
---

### Post by jonathanskinner on 2010-05-03
I was playing Doom using wine and my stupid piece of trash laptop went into suspend mode somehow. This caused the sound to go all high pitched and crappy and the login thing wasn't even working so I unplugged and took out the battery. I have did this many times before when my laptop froze up and would not work at all. But this time after the ubuntu logo on my laptop the screen goes blank and I can't type or do anything on it nothing works. I tried ctrl+alt+f1 but that doesn't work. The only thing that works is ctrl+alt+del for restart. I tried recovery mode and got no where, I can't do anything pretty much. I would go ahead and re-install the stupid garbage if I didn't have very important stuff on. Plus I don't really want to do a re-install. Is there anything I can do to fix this? I already look at some stuff and nothing works. No sounds, no nothing just blank. I'm using Ubuntu 9.1.0 I think. So, any help?

---

### Post by Bietje on 2010-05-03
To begin, use the live option of your install CD to backup all your important data.

---

### Post by jonathanskinner on 2010-05-04
Note: I found a thread with my problem, and it seems to work([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8748384](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8748384)). If not I'll backup and do a clean install. Guess that's pretty much all I can do right now. Its the old No init found. Try passing init=bootarg problem...
 
what the hell is actually going on here i just don't understand what's up with ubuntu. i try the recovery mode, and mounting of /root fails and i only get busybox not a regular sh shell so typing commands like 'sudo' or 'fsck' won't work. honestly what could cause all this destruction? all this from a simple crash of wine? 
 
** Edit ** More info
===============
> mount: mounting /dev/disk/by-uuid/0b35a069-01cd-44c5-940c-187e50524439 on /root failed: Invalid argument
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Begin: Starting AppArmor profiles ...
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
Done.
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init=bootarg
 
And so obviously when I try init 1 it does not work.
 
If I boot up normally I see the ubuntu logo and then it fades to blank and hangs there. I've looked up numerous websites, I guess my only option is to reinstall after backup?? It's a kernel panic isn't it..

---

### Post by jonathanskinner on 2010-05-04
Solved!!

Used live cd, from the terminal I typed:

> sudo fsck -y /dev/sda1and it worked!

Phew..

---

