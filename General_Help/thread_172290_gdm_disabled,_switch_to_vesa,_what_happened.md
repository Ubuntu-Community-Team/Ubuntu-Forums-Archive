---
title: "gdm disabled, switch to vesa, what happened?"
date: 2006-05-08
forum: General Help
---

### Post by leemckusic on 2006-05-08
The problem I have is "What happened", I just recovered from a "gdm disabled" video system failure.
---------------
I fixed it with three trips to these forums by searching under "gdm disabled". 
------------
I am puzzled how could my video X setup get trashed? This is the first time in years that my Linux box has shown a video problem.
--------------
Two days ago I got a "There is a problem starting your x server do you want to view the xorg log files... failure error 11..." and "gdm is disabled" and attempts at startx all looped back to the same error display.
--------------
Right before this problem, I had done a Ubuntu automatic system update... and I noticed something about "the kernel" but I didn't pay attention. 
----
I had also just installed streamtuner and streamripper Debian packages from the Linux Multimedia Hacks book. Two months ago I had installed a Matrox MG400 dual head video card and switched to video card drivers from the Matrox web site.
----
It turns out, I got my system running with advice from the forums here...
[INDENT]First
sudo dpkg-reconfigure xserver-xorg
Second
In reconfigure turn off Matrox MG400 "mga" driver and turn on "vesa"
Third
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start[/INDENT]
--------
So that fixed it. Question: What happened to the system? 
-----------
I initially thought an Xorg file had been trashed due to "streamtuner" hammering on my hard drive while an update program was running in the background. But fsck on "/" showed absolutely nothing wrong. 
---------

---

