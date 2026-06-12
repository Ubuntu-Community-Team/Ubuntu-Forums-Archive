---
title: "GDM Login Screen Blank"
date: 2010-10-25
forum: General Help
---

### Post by SanDiegoSeahawk on 2010-10-25
I'd started another thread regarding my problem, based on the assumption it was VNC related.  Now I'm not so sure.  I've got a 10.4 machine that no longer wants to display the GDM login screen.  I hear the drum beat but the display goes blank and the monitor goes into its standby mode so its not getting any video signal.  I can remotely ssh into the machine and stop GDM.  Last night when I did this I got a non-graphical login prompt on the local host display.  This morning I don't.  The screen comes back but I can't get a login prompt.   Last night I was able to log in (via the non-graphical prompt after stopping GDM), run startx which promptly blanked the display again but I was then able to connect to that Xsession via VNC.  Today I cannot even do that.

I originally thought the problem was VNC related but now I'm thinking it's GDM related.

I saw some posts regarding nVidia drivers and symptoms similar to this and was going to try to update drivers but now I'm not sure how to do that without an Xsession to run the update tool.

Any thoughts on why GDM would be having a problem running on the local host display?

---

