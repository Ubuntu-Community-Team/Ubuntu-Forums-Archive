---
title: "Can't boot - stuck after running rc.local"
date: 2006-06-11
forum: General Help
---

### Post by Mazin on 2006-06-11
During the booting process, it'll go through and tell me what it's doing.  Well, after the first list is done, then it says it's Running boot scripts (rc.local) ok, and after that it doesn't do anything.  Dapper's been working fine for awhile, but this is after I installed a new graphics card.

Does anybody else have this problem?

---

### Post by spaznrq on 2006-07-13
I am having the same problem, and just made a post in this thread before I found yours: [http://ubuntuforums.org/showthread.php?t=201303&highlight=rc.local+boot](http://ubuntuforums.org/showthread.php?t=201303&highlight=rc.local+boot)

---

### Post by souba on 2007-11-10
I have this problem as well. I'm using Gusty and I've chosen my video adapter instead of the default to make use of dual monitors (but it failed, the secondary monitor couldn't get the proper refresh rate). I tried to revert back to single monitor. But after rebooting, it gets stuck on the same textual messages as the first poster had, as in running rc.local [OK], just after the Ubuntu loading screen finishes up the progress bar. Is there any way (command or something) I could use on command line/recovery mode to revert the driver settings back to the default? Thanks!

---

### Post by ngakalden on 2007-12-30
Anyone on this? I am having the same issue. After setting up dual montitors, and loading the graphics card drivers. Totally stuck at "loading local boot script". What do I do now?

---

### Post by flower71 on 2008-03-13
In case anyone who still needs help runs across this message, the solution I found was to set the graphics back to defaults by running this command:

sudo dpkg-reconfigure xserver-xorg

This will start a text-based wizard, giving you the opportunity to accept all defaults or set some custom values.  I've ended up running it several times as I struggle to find a good 2-monitor configuration.

Meghan

---

