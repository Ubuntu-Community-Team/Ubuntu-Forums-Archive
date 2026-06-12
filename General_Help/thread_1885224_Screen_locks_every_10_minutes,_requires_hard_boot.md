---
title: "Screen locks every 10 minutes, requires hard boot"
date: 2011-11-22
forum: General Help
---

### Post by Spink on 2011-11-22
Hey guys,

   I recently dusted off a 2002 Gateway desktop and installed Ubuntu 10.04. It runs great, except the machine is currently unusable because every 10 or so minutes, the display shuts down to a black screen flashing little spastic bursts of white around the edges.  The only option then is to reboot the system; the so-called "magic button combo" of alt+SysReq works in this situation, or holding down the power button..

I've changed every power management option in the panel, unchecking the boxes that make the machine sleep when idle and I've also disabled the screensaver...I also made a bunch of changes in the gnome option list that you can access from terminal, although now I can't remember what the command to get to it was.  

This has been a problem since the I first installed the OS, and although usually it doesn't occur while I'm actively using the computer, there have been a couple times where I've been moving the mouse while it's happened, leading me to believe that it might not be something entirely related to idling...

Thanks for any help!

---

### Post by jerrrys on 2011-11-24
open up your system monitor and look at the processes.  anything there related to screensaver?  if so, kill the process and see what happens

---

