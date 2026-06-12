---
title: "Nvidia Driver Problems"
date: 2012-08-16
forum: General Help
---

### Post by JoshuaRL on 2012-08-16
Hello there everyone.

I've got a hacked together Gateway Desktop, but everything has been going fine until now.

I rebooted into W7, I swear just to watch Netflix, and when I came back, my screen resolution was screwed.  I'm stuck at 800x600, the Nvidia drivers won't activate, and can't find any solution on Google.  Also, no sound is coming out.  I would prefer to not compile and install a driver, or even install a driver from a PPA, but if NOTHING else works I'll try that.

The error I get when I try to install drivers via Additional Drivers is:  Sorry, installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log

Please help.

Computer specs
12.04
2nd Gen i3
4GB RAM
1TB HD
PNY GTX 460Ti
Sony EX700 47" LED TV as monitor
HDMI for video and audio

Pastebin for jockey.log:
[http://paste.ubuntu.com/1150725/](http://paste.ubuntu.com/1150725/)

Pastebin for xorg.conf:
[http://paste.ubuntu.com/1150734/](http://paste.ubuntu.com/1150734/)

---

### Post by JoshuaRL on 2012-08-16
Anyone have an idea?  I really hate to be stuck in Windows, but that resolution is not usable.  I tried going back to an earlier kernel, but that didn't change anything.

---

### Post by JoshuaRL on 2012-08-16
For anyone else that finds this, I think I may have found a solution.  Don't have time to check right now, but will report back later.

[http://ubuntuforums.org/showthread.php?p=10416809#post10416809](http://ubuntuforums.org/showthread.php?p=10416809#post10416809)

---

### Post by JoshuaRL on 2012-08-22
Yep worked well.  I would emphasize the importance of fully removing your current Nvidia drivers and reinstalling them first to make sure though.

---

### Post by bogan on 2012-08-22
Hi!, J**oshuaRL**,

The Link you gave in your Post #3 does not work - PERMISSIONS - could you please edit it, or give a summary of what you did to solve things?

Chao!, **bogan**.

---

### Post by TREESofRIGHTEOUSNESS on 2012-09-23
it seems he fully removed the Nvidia drivers (the proprietary ones I assume) and reinstalling them.  Though it does seem as though more could be involved, eh?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
might also help you

---

