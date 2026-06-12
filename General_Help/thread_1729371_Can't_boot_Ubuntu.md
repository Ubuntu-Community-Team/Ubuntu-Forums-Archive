---
title: "Can't boot Ubuntu"
date: 2011-04-14
forum: General Help
---

### Post by ulfj on 2011-04-14
Coming to you from a liveCD I really don't know what happened here but I can't get my computer to even get to the splash screen heres what happens.

I shut my laptop down last night and when I turned it on this morning I get the toshiba start screen then when it should go to the Ubuntu splash screen I get this error

mount: mounting /dev on /root/dev failed no such directory
mount: mounting /sys on /root/sys failed no such directory
mount: mounting /proc on /root/proc failed
target file system doesn't have /sbin/init 
no init found. Try passing init=bootarg

sorry I wrote this down to post here but that is what I get, usually google and the forums are my friend but I couldn't find a solution.

Any help on this?

---

### Post by lmarmisa on 2011-04-14
Please, go to [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and try to run the Boot Info Script.

Then post the results on this thread.

---

### Post by ulfj on 2011-04-14
Thank you for the quick response lmarmisa, I really do not understand what I just did but I quit the live CD and and restart the computer and it did get to the splash screen and wanted to check the drive so I pressed the f key and it started up fine. I will need to dig into this as this has happened before and I did a clean install (and did one this morning) and all was fine for months, this time it was only for the day so I guess I won't mark this solved quit yet.

Keep the ideas coming as to what may be going on here!

---

### Post by Dutch70 on 2011-04-14
Just a thought, but you may want to open "Disk Utility" and check the SMART data on your hard drive.

---

### Post by Rubi1200 on 2011-04-15
+1 to Dutch70's suggestion to check the health of the drive.

You could also check the logs for indications of what is going on; e.g. dmesg, syslog, and messages logfiles may contain something that can help you troubleshoot this.

---

