---
title: "Desktop Tiling"
date: 2006-02-08
forum: General Help
---

### Post by austinhow on 2006-02-08
Hello, new to Ubuntu and somewhat new to linux.  I have a strange problem of my desktop tiling over itself on the left & right sides.  Im using a Dell 2005 flat panel monitor and have the resolution set to 1600 X 1050.

When I drag a window over to either side of the desktop it starts to show up on the opposite side. It seems that a pretty good chunk of the desktop is effected by this... almost like its stuck in a 1280 X 1024 desktop size centered on my screen even though the OS is displaying the proper resolution.  Also my top and bottom panels are suffering from the same effect by bleeding over to the opposite side.

Has anyone experienced this?  This has been been an absolutely flawless installation except for this little problem and searches on the forum are not coming up with any fixes.

thanks
Austin

---

### Post by austinhow on 2006-02-08
One bump because I can't figure out what the problem is.

---

### Post by nik on 2006-02-08
Don't know, but I had could only see half the desktop at some point, like my screen was twice as big as it really is... 

Post your /etc/X11/xorg.conf and maybe we can figure it out. Also, what kind of graphics card do you have?

---

### Post by austinhow on 2006-02-08
Thanks for the reply.  I will post xorg.conf tonight after work.  As far as video cards go I have a ATI 9800XT.  I havent updated the drivers for it yet as it was initally recognized by the system and was just trying to get the desktop setup like I wanted it.  Should note that the everything looks quite good on screen at the resoultion I specified ... only the gnome desktop is having issues atm.

---

### Post by austinhow on 2006-02-08
Ok figured it out.  

Somehow some screen resoltuions appeared on selection box that weren't listed in the xorg.conf file.  I have no clue how they got there, but I was set up for widescreen displays after my first restart... I think Gnome was looking at xorg.conf file for 1680x1050 resolution and couldnt find it so it set it at the highest setting it could which was 1280x1024 which caused the strange overlap.  Edited the xorg file and all is well.

---

