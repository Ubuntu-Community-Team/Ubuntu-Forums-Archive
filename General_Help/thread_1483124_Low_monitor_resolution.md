---
title: "Low monitor resolution"
date: 2010-05-14
forum: General Help
---

### Post by StephanG on 2010-05-14
Hello everyone,

I recently bought an LG Flatron W2243S Monitor.  A 22" Monitor with a native resolution of 1920x1080.  But it had a maximum resolution of 1024x768, even after installing the latest Nvidia graphics cards.

So, off I went in search of a solution.  There are countless Xorg configurations and tweaks on the web and I felt like I've tried them all, each one managing to screw up my system more than the previous.  In my endevors, as I grew increasingly desperate I reinstalled my OS no less than 7 times.  (My new monitor overlapped with my upgrade to 10.04, so no major loss.  I had already backed up everything.  And yes.  I do know how to backup the xorg.conf file and restore it from console.)  I even tried escaping to windows.  WINDOWS!  But the problem persisted.  Haunting me.  Taunting me.

But finally I discovered the solution from my brother.  He told me to switch to the DVI-D port on my graphics card.  (I believe most graphics cards have one nowadays.)

So, I switched to the DVI-D port using a converter that came with the monitor, and turned the PC back on...

And VOILA!  It booted up into the native resolution of 1920x1080, perfectly detecting my monitors capabilities.  I didn't even have to set the resolution.

And thus my story comes to a close, as I posted this here.  In the hopes that it may save someone else the 10 days of misery it cost me.

P.S.  If the screen turns purple after you switched, it just means that its not connected properly, just twiddle with the connection a bit.

---

