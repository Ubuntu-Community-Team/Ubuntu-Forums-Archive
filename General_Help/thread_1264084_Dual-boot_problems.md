---
title: "Dual-boot problems"
date: 2009-09-11
forum: General Help
---

### Post by Essary on 2009-09-11
I've installed Jaunty and WinXP. Got everything set up in WinXP, then I switched over and started working on Ubuntu for a couple of days. Now when I try to boot into XP it seems to get all the way in, loading the programs that run at startup, and then turns off the computer. Ubuntu is working fine. Is there something I could have done while in Ubuntu to cause this problem. All I have done is install media players and codecs, and deleted one .wmv file, surely none of this could have caused problems. Booting XP in safe mode works fine, but I don't know what to fix. The only option I know of is system restore. Haven't tried it but I would like to know what the problem is either way.

---

### Post by blueridgedog on 2009-09-11
I suspect you installed a bad driver as part of getting windows "working fine" and are just noticing it now when you try and boot into windows.  System restore in this case if it were me.  I create a restore point before each driver install for this reason.  Give it a shot.

---

### Post by Essary on 2009-09-11
I tried system restore, no luck.

---

### Post by Irvine_himself on 2009-09-11
Boot in safe mode goto

control panel >> administrative tools >> event viewer


It is mainly "system events" that you are checking, but check the rest just in case. Bad things are marked with a big red cross. When you double click an item you get  a moderately detailed report. You should be able to find out why it shutdown.

Failing this, while still in safe mode, successively start services that are marked automatic

control panel >> administrative tasks >> services

You might need to adjust the size of the window to see the start-up type, use the extended pain and you will see a link that lets you start the service. Alternatively, double clicking the entry brings up detailed card with various options.

Use  bit of intuition, if it say's it needs another service then try and start that service. Finally, if you still have not identified the problem start your normal "start-up" programs. 


Doing this won't fix the problem, but you will at least have a better  idea of what the problem is!

PS

If selectively starting services/programs, it may seem an oxymoron, but remember to write down each successive step. You would be amazed at how many times I have been embarrassed thinking "Oh it's okay, I will remember!"

---

