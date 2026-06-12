---
title: "Screen Resolution Woes"
date: 2011-02-14
forum: General Help
---

### Post by carlito_h on 2011-02-14
Hi there, everyone. I recently upgraded my desktop pc from 10.04 to 10.10 and ran into a tad of trouble. After I attempted to login from the GDM, something  caused the system to crash and return to the GDM. So, I got my laptop out, did some googling, and decided to delete ~/.config/monitors.xml to try and reset the resolution. That got me to the Desktop, at which point I was greeted by more display issues. 

The point at which the computer normally goes idle seems to crash and return it to the GDM as well. Needless to say, I disabled the idling/password prompt setting to prevent crashes every five minutes. Anyway, the prevailing problem is that I can't change the resolution itself -- as that seems to cause the same issue.

Has anyone else had this problem? If not, any suggestions?

---

### Post by Gerry07 on 2011-02-14
Had some trouble myself after this upgrade. What fixed it for me was re-installing my graphic drivers(Nvidia) from the command prompt. Like this:
 
sudo sh "Path To Driver File/Filename". 
 
Typically you will be asked to uninstall the previous version even if it is the same, do this and then the install will continue. Good luck.

---

### Post by carlito_h on 2011-02-15
Seems to be a recurring problem amongst those with my graphics card. Using the S3 ProSavage8 KM266/KL266, which seems to rely on the driver contained in *xserver-xorg-video-savage*.

There are quite a few threads involving quirks with the card, but I didn't see any solutions. If all else fails, I can invest in a graphics card. :) Bumping once, though.

The chipset isn't listed as supported on it's manpage, and if no one says otherwise, I'll assume that's the problem.

[http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/savage.4.html)

---

### Post by carlito_h on 2011-02-25
Alright, I thought I'd come back add the solution just in case anyone else has this problem. I found the link below before I posted this thread, but I think got the monitor identifier wrong, which essentially left me with a terminal screen. What appears to be needed is an xorg.conf file, the nature of which is detailed here:

[http://ubuntuforums.org/showthread.php?t=1603534](http://ubuntuforums.org/showthread.php?t=1603534)

This worked for me. I can let my computer go idle again, open things that involve resolution adjustments, and all that jazz.

---

