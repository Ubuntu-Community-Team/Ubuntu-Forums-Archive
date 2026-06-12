---
title: "Jaunty / 9.04 freezing on shutdown"
date: 2009-08-20
forum: General Help
---

### Post by dreamingdarkness on 2009-08-20
So, I noticed some issues after applying a work-around to one of my libraries to remove problems with 9.04 mounting/recognizing my Sansa MP3 player.

It hangs on shutdown, giving the following as the last two seconds of system log:
```
Aug 19 03:27:16 ubuntu console-kit-daemon[3060]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Aug 19 03:27:16 ubuntu last message repeated 2 times
Aug 19 03:27:16 ubuntu init: tty4 main process (2593) killed by TERM signal
(bunch of TTY shutdown and wlan0 shutdown snipped here!)
Aug 19 03:27:17 ubuntu nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 19 03:27:18 ubuntu console-kit-daemon[3060]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Aug 19 03:27:18 ubuntu console-kit-daemon[3060]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Aug 19 03:27:18 ubuntu console-kit-daemon[3060]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
```

In worst case, I can re-install the new/original/official packages back over the patchwork results and get my laptop working right with shutdowns, but it means charging and syncing my MP3 player from Vista on the laptop - essentially, using it for all my media library functions. I've managed to make it almost 4 months since last booting into my Vista partition, and I would love to keep that rolling.

Any advice? Be honest, even if the advice is "Nuke your slap-patch fix".
(FYI, fix to make Jaunty load the Sansa was from [http://randynoseworthy.blogspot.com/2009/05/sansa-e200-seires-not-mounting-bug.html](http://randynoseworthy.blogspot.com/2009/05/sansa-e200-seires-not-mounting-bug.html), used the code from the comments. One problem solved, another problem created. Playing whack-a-mole eternally!)

Thanks

---

### Post by tgeer43 on 2009-08-20
Are you certain that the shutdown problem is the result of your workaround or could it be coincidental?

For starters, I'd suggest you "Nuke your slap-patch fix" (your words, not mine) to see if it resolves the problem since you can always re-patch it if not. This will go a long way towards troubleshooting the issue.

If un-patching does correct the shutdown problem and the workaround is a multi-step process then try applying it one step at a time and shutdown in between steps. This should narrow it down to a single problematic step or command and we can go from there.

You can also try googling each of the last four error messages (minus the timestamp, of course) to see if that sheds any light on the situation.

BTW: Your post already shows up in Google when searching on the first line of code that you provided. Less than 30 minutes after you posted. How's that for efficiency. I read an article on Google and their server farms are unimaginably large and powerful. Over 500,000 servers - all running Linux, of course!

tgeer

---

### Post by dreamingdarkness on 2009-08-20
Thanks for the advice. I will probably de-patch myself with an update, get all my kernel upgrades/etc, and see if the MP3 player works - then re-patch step by step, or at least as much so as is possible, if the shutdown issue goes away. It's true it may be coincidental, rather than cause, since the patch was done only a day or two (memory, gone already, before 30) after the 8.10-9.04 upgrade.

Funny part is I had a boot-freeze on 8.10 that was reportedly (and is, in fact) fixed by 9.04. It also fixed by 8.10 NetworkManager failures, though that was easy to fix by killing and re-initiating the task once startup completed. 
Thanks again, tgeer43!

(As for Google - yeah, that's pretty impressive. All the other mentions of the same error seem to be older - so sadly no help there. Well, time to experiment! Fortunately, my pre-upgrade prep-work involved backup up all my packages, files, and other miscellanea to an external drive, so I can't loose too much!)

---

