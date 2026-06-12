---
title: "Firefox Crash Once After Boot"
date: 2009-11-24
forum: General Help
---

### Post by give.away on 2009-11-24
Don't know it this is a OS or FF related problem:
Firefox crashes the first time I start it after boot. Further starts are perfectly fine.
What might be the reason? Has anybody encountered the same problem.
Perhaps it's plugin related, but I don't want to restart my computer for every plugin to test it ;)
Is there some kind of error console?

Thank you!

---

### Post by varangian on 2009-12-07
My own experience may shed some light on yours - I was going to start a new thread but searching for Firefox problems (rather too many of those for my liking) found this which is close enough and could do with a bit of attention.

I did a clean install of 64 bit 9.10 and swiftly ran into a problem familiar from my previous Gutsy installation. This is that in Ubuntu/Linux shutting down the OS is interpreted by Firefox (3.5.5. and earlier) as a crash for no very good reason. Call me lazy if you like but I don't think I need to go round doing File/Quit on every open application when I reboot/shutdown and no other application has a problem handling this. To add insult to injury Firefox in Windows behaves as you'd expect, shutting down the OS is a clean shutdown for FF.

The effect of this is that when FF has been terminated by the OS the next time it started up a bunch of unwanted tabs materialised and started loading up. I knew how to fix that as I'd had to do the same in Gutsy, so I set browser.session.resume_from_crash to false.

Unlike in Gutsy, however, this had an unexpected side effect, the one mentioned by the OP. With this setting launching FF would start it up but no window would instantiate and a few seconds later the process would die. Launching it from the command line had the same effect and produced no error messages. On the second launch it would start up with no sign of a problem.

I did a bit of experimenting and found a presumably related effect. With resume_from_crash set true I started FF and immediately shut it down and restarted. This usually worked as it should - the close/restart cleared the spurious crash recovery and just went to the home page - but a couple of times I got it into a repeated cycle. On the second start I'd get a 'Firefox process already running' message and no window would instantiate. Looking at the process list there was indeed a FF process running. Further starts of FF produced the same effect but the process id kept changing as if a new process was actually starting but then refusing to instantiate for some reason. Perhaps this is a clue as to the cause of the main problem - is FF not actually terminating properly under some circumstances?

Once FF is actually running I've found these OS/FF iterations give me a much better experience than in Gutsy where I'd get frequent Flash related freeze ups. It's irritating that it's being spoiled by glitches like this.

---

