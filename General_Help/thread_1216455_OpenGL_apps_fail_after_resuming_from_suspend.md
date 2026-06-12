---
title: "OpenGL apps fail after resuming from suspend"
date: 2009-07-18
forum: General Help
---

### Post by flar on 2009-07-18
I'm using Ubuntu 9.04 (jaunty) with Nvidia driver version 173 and not using compiz.

I have suspend to RAM working, and resume works fine, except that when I try to start apps that use OpenGL after resuming, they terminate.  Otherwise, everything comes back normal.

The application I want to use is xbmc (which uses openGL). It works fine before suspend, but after resuming, it crashes immediately and leaves the screen resolution at a low res (like 640x480).  I could not get any debug info from xbmc.  I can use the computer just fine after the crash, there is no lock up or anything.

To test further, I tried to run planetpenguin racer (also uses OpenGL).  It runs fine before suspending, but after suspend it also crashes immediately and leaves the screen in a low resolution.  

If I logout and login again (or otherwise restart X), everything is back to normal (i.e. no reboot is required to get things working again).


Does anyone have experience with this problem, or know any fixes?

I can provide more details if needed.

---

### Post by NightwishFan on 2009-07-18
I has a similar problem with hibernate. Any gstreamer applications would be silent after resuming. This problem was fixed when I chose to use 64-bit instead of 32-bit. Although I might have just been lucky. :D

Perhaps run an OpenGL program in the terminal, and see the message when it crashes.

---

### Post by flar on 2009-07-19
^^I tried running them in the terminal. I couldn't get any debugging info.  Both just said "Aborted" and that was it.  

I am hoping someone could give me some clues about this.  Google searches about suspend, resume, nvidia, opengl, etc. brings up a zillion hits, I don't have time to sift through it all and I've already solved the issues most of those hits discuss.

---

### Post by flar on 2009-07-19
I should mention that glxgears does the same thing, it just says "Aborted" and terminates.

---

