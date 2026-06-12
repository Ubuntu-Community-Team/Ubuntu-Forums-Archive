---
title: "EEEPC 1001p/Ubuntu 10.10 - Constant Crashing, No Touch Pad, Sound Dead"
date: 2010-12-04
forum: General Help
---

### Post by modustollens on 2010-12-04
I am trying to solve, on my EEEPC 1001p running 10.10, the following problems:



(1) Sound is dead.  It was working fine; but after a OS crash (see 3) it did not start to work once the reboot occurred;

(2) Mouse Touch Pad is dead.  It was not working after the initial install.  I read some threads about this and updated the BIOS on the EEEPC - then the mouse pad worked until a system crash (see 3) after which the mouse pad would not work any more.  (The BIOS update corrected the screen brightness control).

(3)  Fatal Crashes: the monitor screen goes black save for the mouse indicator.  Nothing will take the system out of this state save for turning the power off and rebooting.  

Error 3 will occur if I run compiz or not; if I keep my wireless mouse connected or not.

Error 3 did not occur when I told ubuntu to start a 'save-desktop' session.

I looked at the error logs but I am far from sufficiently knowledgeable to know exactly what I should be looking for; nonetheless I did not see anything in the error logs that had 'E' for error.

Somewhere on some thread I read someone suggested that re-writing the XORG.conf file would be a prudent thing to do.  I thought I would just now look at that file; so I terminaled:

sudo gedit /etc/X11/xorg.conf


When the file opened all that was contained in the file was the number 1.

That makes me suspect there is something wrong here for I remember looking at that file a long time ago when I had a problem with 8.04 and I believe it had a lot of information it it.


I spoke with a friend of mine who I usually speak to on computer matters and he suggested I reinstall.  That's not something I wish to do - too much work.

Any suggestions from this crowd will be more than welcome.

Thanks.

MT

---

### Post by modustollens on 2010-12-05
Update:

I was looking at the hidden file called 

.xsessions-errors in my home folder.

It showed the following error:
[INDENT]
Failed to stat runtime directory /home/modustollens/.pulse/4d562d1e3b00538a1a2b485c00000007-runtime: Invalid argument

** (gnome-settings-daemon:1427): WARNING **: Connection failed, reconnecting...
Failed to stat runtime directory /home/modustollens/.pulse/4d562d1e3b00538a1a2b485c00000007-runtime: Invalid argument
Failed to play sound: Not available[/INDENT]


I deleted the .pulse file and restarted pulse audio - now the sound is back up and running.

I still have no solution for (2) - which is not critical for I always use and external mouse anyway; but issue is (3) is critical and I would welcome any suggestions about how to diagnose and repair the problem.

MT

---

