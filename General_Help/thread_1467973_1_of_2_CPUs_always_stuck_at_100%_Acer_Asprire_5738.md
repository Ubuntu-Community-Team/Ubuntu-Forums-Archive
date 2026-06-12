---
title: "1 of 2 CPUs always stuck at 100% Acer Asprire 5738G Dual Core"
date: 2010-05-01
forum: General Help
---

### Post by xrono on 2010-05-01
Dear community,

I have fresh install of Ubuntu 10.04 LTS
Added Wine from Software Center but have no any Win apps loaded or running yet.
I have also enabled visual Effects and the system installed and enabled NVidia's driver for the video-card after which the picture quality improved.
Here is the screen of my CPU monitor (sorry labels arre in Russian but the charts are quite intuitive)
[U][[IMG]http://img710.imageshack.us/img710/9330/cpu100.th.png[/IMG]]("http://img710.imageshack.us/i/cpu100.png/")

[/U]As you can see this 100% load "jumps" from one core to another periodically.
On the Processes tab there is nothing fancy:
[[IMG]http://img144.imageshack.us/img144/4206/processes.th.png[/IMG]]("http://img144.imageshack.us/i/processes.png/")

Less than 10% processes load.

I have tried to play with CPU Clock Gnome widget, it doesn't really change the picture whether I use MAX CPU clock of 2Ghz or reduced power-saving 1,2 GHz. 

I have found couple similar cases on forum but see no solution so far.
BTW, I have already launched the update manager and currently Ubuntu does not offer any new updates.

[http://ubuntuforums.org/showthread.php?t=1416324](http://ubuntuforums.org/showthread.php?t=1416324)
[http://ubuntuforums.org/showthread.php?t=1437330](http://ubuntuforums.org/showthread.php?t=1437330)

Thanks.

PS. In the attachement - Report of some built in System Diag Tool

---

### Post by xrono on 2010-05-01
[IMG]http://img227.imageshack.us/img227/2545/backend.png[/IMG]
Who can advise what is "backend" process?

---

### Post by Queue29 on 2010-05-01
You aren't the only one...

[http://ubuntuforums.org/showthread.php?t=1466877](http://ubuntuforums.org/showthread.php?t=1466877)

[http://ubuntuforums.org/showthread.php?p=9204451#post9204451](http://ubuntuforums.org/showthread.php?p=9204451#post9204451)

[http://ohioloco.ubuntuforums.org/showthread.php?t=1453980](http://ohioloco.ubuntuforums.org/showthread.php?t=1453980)

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

---

### Post by dino99 on 2010-05-01
i think that all the multi-cores works like that :P because the others could be jalous :lolflag:

---

### Post by xrono on 2010-05-01
> **Queue29 said:**
> You aren't the only one...

[http://ubuntuforums.org/showthread.php?t=1466877](http://ubuntuforums.org/showthread.php?t=1466877)

[http://ubuntuforums.org/showthread.php?p=9204451#post9204451](http://ubuntuforums.org/showthread.php?p=9204451#post9204451)

[http://ohioloco.ubuntuforums.org/showthread.php?t=1453980](http://ohioloco.ubuntuforums.org/showthread.php?t=1453980)

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

Thanks for all the links.

Actually I think I found a remedy after reading through.

First of all, I could not kill processes because of priveleges.
I do not remember setting root password during the install, so according to some post that worked for me:
> sudo passwd root
You will be prompted to enter your current account password and then you can set new password for "root".
Now, you switch to "su" mode:
> su -
You will be prompted for the root password that you set up in the previous step. Enter it and see that command prompt now has symbol "#" at the end meaning that you have superuser privileges now.
Run top (you can also run "htop" if it is installed and use GUI-like interface to highlight and kill processes)
> top
Take a note of Process ID for "backend" process. In my case I have TWO!! processes each having 100% CPU. Both Cores now were 100% loaded (in the beginning of the post there was only one! Have no idea when and why the second appeared)
Run
> kill -9 process_id

Now Load is less than 10% on both cores working at lowest clock 1.2 GHz

Expecting the laptop to cool down :)

---

### Post by kshep92 on 2011-09-02
Hi, 

Do you have to do this process every time you boot up the machine or is it a one-time only deal?

Also, have you found out the real reason why this happens?

I have been experiencing the same issues on my Aspire 722.

---

