---
title: "Vertical blue line on screen"
date: 2012-06-08
forum: General Help
---

### Post by Ampi on 2012-06-08
Since I upgraded from Ubuntu 10.10 I have a blue vertical line appearing on the screen. It has never been there before so I cannot imagini it being problems with the screen (Samsung SyncMaster T220), the screen is also fairly new. 

Even stranger, the line doesn't seem to be part of the image showing nor the screen as its visibility changes. It seems to depend on background colors, but it doesn't show on any printscreen no matter when I take it.

I have attached two photos, one is the photo of my desktop where the entire vertical line is visible and the other one of the Ubuntu forum, in which the line is only visible on the orange part and other darker colors. If I move another window over the not visible line, it becomes visible again on darker parts of that window.

I seriously have no clue how to go about it and I also have given up on Google. I am open to any suggestion so if anyone has a clue you will be more than welcomed!

---

### Post by dino99 on 2012-06-08
the basic questions:

- is  ppa used, in case purge it (sudo ppa-purge ...)
- erase xorg.conf to let the kernel dealing with X (sudo rm /etc/X11/xorg.conf)

- is it the same issue if you change the desktop ? (unity, shell, gnome-classic)

maybe a compiz or compiz-plugins issue : again purge then reinstall by step

---

### Post by kanikilu on 2012-06-08
Does the line show up when you first turn the computer on? During POST, or in the BIOS, for example? Does it show up if you boot up with the Live CD? If so, it's probably hardware-related. If not, it may be a driver issue.

I think I've seen this once before on a laptop, and it turned out to be bad hardware (eventually there were multiple lines running down the screen).

Since you mentioned the Samsung, I'm assuming this is a desktop with external monitor. This could be as simple as a loose cable. Make sure that the monitor cable is secure - check both the monitor and computer ends. If you have a discreet graphics card, check that it's firmly seated.

---

### Post by Ampi on 2012-06-08
Thank you for the quick replies!

@dino99: With the ppa being used, do you mean for a specific program or something else? Because I couldn't find good answers a year ago I stopped trying and I have been installing and removing programs ever since, sometimes with ppa. Blue line never changed anything. I cannot do a fresh reinstall this month but next month I can and hope that that might help. If I remove xorg.conf, the system will make a new one itself? Compiz is not installed but I'll try the change of desktop to see if that gives any changes tonight. Thanks!

@kanikilu: It is indeed an external monitor, cables seem to be attached good, and I don't have a seperate video card, just on the motherboard. I will restart my computer tonight, when my sims have finished and try with the LiveCD, but I don't remember the blue line showing up during boot. Good tip!

---

### Post by Ampi on 2012-06-12
The blue vertical line shows up also during boot, LiveCd and another desktop. It does disappear every once in a while for a very short time during boot, but I think that is during boot where the screen is suppose to go black anyway. 

Just in case I made a video of it: [http://vimeo.com/43883324]("http://vimeo.com/43883324").

Is there anything else I can try? 

If not then I'm just hoping it doesn't get worse. It hasn't since at least a year...

---

