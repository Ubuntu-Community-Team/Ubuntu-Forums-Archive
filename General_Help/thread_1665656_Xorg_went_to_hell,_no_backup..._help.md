---
title: "Xorg went to hell, no backup... help?"
date: 2011-01-12
forum: General Help
---

### Post by elchato on 2011-01-12
Hi, I was trying to get dual monitors to work with Nvidia's gui and and when I restarted the xserver, it wouldnt come back into nautilus, so... Im stuck in the command line trying to reconfigure the xserver, however, when I give it the command to do it (sudo dpkg-reconfigure xserver-xorg), it just wont start the reconfiguration.

So, I found a xorg.conf backup, but when I try to rename my old xorg.conf and the xorg.conf.backup, I get this message 

Bareword "xorg" not allowed while "strict subs" in use at (eval 1) line 1
 WHAT THE HELL IS THAT?

Thanks!

---

### Post by Tamlynmac on 2011-01-12
I think you may benefit from [this]("http://ubuntuforums.org/showthread.php?t=706488").

Especially, [zvacet]("http://ubuntuforums.org/member.php?u=79320") post.

Basically, it provides you with the ability - to copy your "xorg.config.back" to your "xorg.config"

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf 
One thing to consider prior to running this command, is the date the  backup file was created. If it was created after you corrupted the  original xorg.conf, then it may not improve your situation (as it would  be a copy of your modified file). If so, you may wish to check for other  xorg.conf files in the etc/X11 directory. For example there may be a  xorg.conf_backup or xorg.conf.failsafe that will get you started again.  Simply alter the command to copy one of those instead of the  xorg.conf.bak

Also, don't forget (prior to running the command) - to make a copy of your  modified xorg.conf file for reference and to help you alter the new xorg.cong file  appropriately.


*** One future suggestion: when trying to alter any critical file, make a  copy of said file prior to altering and store it for easy access. That  way should something go wrong you simply replace the corrupted file with  the original saved file. Just some words of wisdom.


Good Luck & hope this helps

---

