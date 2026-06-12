---
title: "Random purple screen of death"
date: 2010-12-13
forum: General Help
---

### Post by Ingenium on 2010-12-13
I'm currently running Ubuntu 10.10 on a Thinkpad T400 with ATI graphics (using fglrx). I regularly, ie once every 1-2 days, get a "purple screen of death", where the screen just randomly turns purple with vertical white lines (see attached screenshot). There is no consistent pattern to when it happens, although there is a higher likelihood of it occurring during/after playing a video. Today it happened 2 hours after a fresh boot while I was scrolling on a web page (no flash in any tabs); I hadn't played any video nor loaded any virtual machines. The only thing running was Chrome with a couple tabs open.

This has been happening since I got this laptop last October and installed 10.04 on it, and I've tried upgrading to the latest fglrx drivers every month, but it's never fixed it. In fact, November's release of fglrx seems to make the problem worse (multiple times a day), so I've reverted back the version that came with 10.10.

I can't seem to find anyone else with this problem, except when booting the livecd for installation. 

Is this a graphics issue? Some other issue? Anyone else have this problem?

---

### Post by Ingenium on 2010-12-29
bump. Anyone? It seems like it could be related to this thread, [http://ubuntuforums.org/showthread.php?t=1605768]("http://ubuntuforums.org/showthread.php?t=1605768"), but I don't have an AMD CPU so the "cool n quiet" BIOS feature isn't there.

---

### Post by J V on 2010-12-29
It's probably an error with X...

Try hitting ctrl alt f1 then logging in in the terminal, see if it still works...

---

### Post by Ingenium on 2010-12-29
Thanks, but I've tried that and it unfortunately doesn't work. Even the sysrq commands to "safely" reboot the system do nothing (I have them enabled and they work any other time). The system is completely unresponsive to anything. If there's music playing when it happens, the last 1-2 seconds of whatever was playing just loops over and over until I hold down the power button to shut it down. It's pretty much a hard lockup.

---

