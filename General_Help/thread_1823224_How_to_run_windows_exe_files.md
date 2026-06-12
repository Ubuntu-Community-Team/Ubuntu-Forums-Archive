---
title: "How to run windows exe files?"
date: 2011-08-11
forum: General Help
---

### Post by davy jones on 2011-08-11
Can anyone please tell me how to open exe files which are meant for windows in ubuntu 10.04 (lucid lynx)? They always give some sort of error in archive manager. Help would be much appreciated

---

### Post by oldos2er on 2011-08-11
Please read the stickies at the top of the Wine forum: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by davy jones on 2011-08-12
Thank you. So I installed wine and I managed to install the software I wanted to install, which is Samsung Allshare for my blu ray player, but now the problem is that the software won't run. When I click on it, a "starting samsung allshare" window appears in minimized mode in the bottom panel but closes after a few seconds and that's it. There are no error messages or anything but it just won't open. Any suggestions?

---

### Post by robgr85 on 2011-08-12
> **davy jones said:**
> Thank you. So I installed wine and I managed to install the software I wanted to install, which is Samsung Allshare for my blu ray player, but now the problem is that the software won't run. When I click on it, a "starting samsung allshare" window appears in minimized mode in the bottom panel but closes after a few seconds and that's it. There are no error messages or anything but it just won't open. Any suggestions?

I would check the log files, maybe there is some hidden message ;)

Wine allows running lots of windows applications, but not all of them. You could try to install ms windows on virtual machine (virtualbox, or vmware), it takes a lot of space and effort, but sometimes it is the only way to go (I have win-printer that won't work under linux, and it works from virtualbox installed on my ubuntu :) ).

---

### Post by aeiah on 2011-08-12
> **davy jones said:**
> Samsung Allshare

from a quick google, i think samsung allshare is just a DLNA server, for streaming things to samsung devices over the network, no?

you'll often find that wine won't run things properly (check their compatibility database for info). the thing is, a lot of the time there'll be native linux programs that'll do the job just fine.

you might get better results from using one of these to stream to your device, if that's the intended purpose.

perhaps mediatomb (this thread might be relevant [http://ubuntuforums.org/showthread.php?t=1198689](http://ubuntuforums.org/showthread.php?t=1198689)), minidlna, rygel or ushare

---

