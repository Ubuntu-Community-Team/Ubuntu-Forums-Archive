---
title: "computer boots up when mouse moved (not hibernating!)"
date: 2006-04-15
forum: General Help
---

### Post by ekarni on 2006-04-15
My computer will boot up by itself when I move the mouse, before I even hit the power button!  No, its not hibernating or suspended, I'm quite certain that I'm selecting the shutdown option, not hibernate from the logout menu.  I also tried shutdown -h now, afterwhich I can still boot this way.  BIOS is not showing any options that seem related.

I first noticed this a few days ago when I tried to get fancontrol to run at startup, per [this]("http://www.ubuntuforums.org/showthread.php?t=42737") thread.  (I never got it to start automatically, and removed all auto-start stuff after I noticed the boot problem).  However, it is very possible that this existed before, and I just never bumped the mouse before hitting the power button.  The next earliest system change was a bunch of updates a few weeks ago -- could one of them be responsible?

So, where does the troubleshooting path start!?  Anyone else run into a similar situation?  Machine is a homebuild desktop system, AMD64 3000, MSI K8TNeo2 motherboard running 32 bit Breezy.  This isn't a critical problem, just something I'd rather not have happen.  Thanks!

---

### Post by Ramses de Norre on 2006-04-15
The boot process has nothing to do with linux, windows or any other operating system..
Untill the POST is finished they can't do anything.. So I guess it's something with your bios..

---

### Post by xXx 0wn3d xXx on 2006-04-15
As Ramses de Norre said above, it is a problem with your bios. Try restoring the default settings in your BIOS. That should fix everything.

---

### Post by ekarni on 2006-04-16
Good call guys.  I dug a little deeper into the BIOS and disabled "wake on mouse."  Problem solved.  However, I'm still curious why that feature was active if the computer was supposedly shutdown - it sure looks like a wake from sleep mode feature.

---

