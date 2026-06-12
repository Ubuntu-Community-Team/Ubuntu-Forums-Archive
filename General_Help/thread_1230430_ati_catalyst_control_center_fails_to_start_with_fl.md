---
title: "ati catalyst control center fails to start with floating point exception"
date: 2009-08-03
forum: General Help
---

### Post by codejammer on 2009-08-03
I was trying to get the TV out functionality working and making edits to the xorg.conf file.  Knowing that this was risky I made a backup. After making the last change the ATI Catalyst Control Center failed to start and when started from the command line using amdcccle gave a floating point exception error.  So I put my backup of xorg.conf back figuring that it would fix the problem since that was all that had changed but it didn't.  Now I cannot get the control center to open at all.  I've even tried re-installing it.  Using fglrxinfo returns...

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300 
OpenGL version string: 2.1.8395 Release

So I assume that the X server is running ok.... any idea as to what's gone wrong?

---

### Post by marcellux on 2009-08-17
I had a similar problem. I could not find any solution. I saved all of my data on an external hard disk and I re-installed UBUNTU.  After that, I will keep away from ATI catalyst center and Co.

I hope you find a better solution than me!

---

### Post by codejammer on 2010-02-18
No I ended up resorting to the same solution ](*,)

---

