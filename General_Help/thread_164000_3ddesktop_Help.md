---
title: "3ddesktop Help"
date: 2006-04-21
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-21
After installing 3ddesktop, I try to start it with the command 3ddesk but I get some error messages:

> chris@ubuntu:~$ sudo 3ddesk
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.

Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

Any ideas on how to fix this ?

---

### Post by bluevoodoo1 on 2006-04-22
What video card are you using?

---

### Post by trent dillman on 2006-04-22
Are you running Xgl?

---

### Post by xXx 0wn3d xXx on 2006-04-22
I have an ATI Radeon Xpress 200M. No I am not using XGL.

---

### Post by djsroknrol on 2006-04-22
I'm running a Radeon 9200 SE and it works fine for me...I've got it set up so I hit CTRL F1 and it comes up...I'm using the Radeon driver ...I'll look up my notes and try to post back...

---

### Post by djsroknrol on 2006-04-22
OK...try this...

after DRI section in xorg.conf, I put a "extentions" section...

Option "Extentions"
Option "Composite" "Enable"

that might help, but it seems like you have something else in there as Trent Dilman suggests...check that out..

---

### Post by creed_1977 on 2006-12-06
Is there a wiki or a guide on how to install the 3ddesk I am on a Compaq v2000 laptop Vid: ATI Radeon xpress 200m

---

### Post by maniacmusician on 2006-12-06
Guys, sorry to give you the bad news (creed and Own3d), but support for your card sucks on linux. from the error you were getting, Own3d, it's obvious that your current drivers don't support direct rendering. I feel your pain; I have an onboard Radeon Xpress 200 in my desktop and it absolutely sucks. I'm pretty sure its closely related to your card. 

Last I heard, the fglrx drivers weren't working with your card or mine, so i don't think there's any way you can get direct rendering. the open source driver won't support it for sure. I've recently bought a Nvidia card though and am planning to use it when I reinstall ubuntu. However if you do find a way to get your card working, let me know, because it will mean that mine will work as well.

edit: saw an older thread of yours; it looks like you said you had gotten DRI working (back in may). so whats the output of glxinfo|grep "direct"  ?

---

