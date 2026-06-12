---
title: "Swap space fills up"
date: 2009-07-07
forum: General Help
---

### Post by nr0mx on 2009-07-07
In the last few weeks, the system runs out of swap space in a couple of hours of normal usage ( firefox, banshee, thunderbird etc ). The hard disk gets real hot and there's constant I/O. Very soon the system is unusable, especially if you try switching apps. 
I thought it was due to an issue with the intel video drivers, but the problem is still there after the last system update which seemed to have a fix for the video drivers. Around the time the system gets unusable, the /usr/X11R6/bin/X process is using up around 433M of virtual memory according to top. 

Anyone else face this issue ?

Update: I've been restarting X from the tty when this happens ( sudo /etc/init.d/gdm restart ), which effectively resets swap space usage back to 0, but that's hardly a satisfactory solution.

---

### Post by mlang on 2009-07-07
I have seen this in the past with firefox, try killing firefox from a virtual terminal, then if I remember correctly my flash plugin was the issue.

---

### Post by nr0mx on 2009-07-07
Thanks, but I've see swap space rise even when Firefox isn't running. Also, when I close down any of the apps, including Firefox, swap space doesn't come down proportionately. 

It would appear that my Ubuntu install is bitten by this bug:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328232](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/328232)

That seems to be the best guess at this time.

---

