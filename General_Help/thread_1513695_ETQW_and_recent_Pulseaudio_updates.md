---
title: "ETQW and recent Pulseaudio updates"
date: 2010-06-19
forum: General Help
---

### Post by MichiganMan on 2010-06-19
So the recent Pulseaudio updates have been increasingly at odds with Quake Wars, a game near and dear to my heart.  Minor irritations like occasional instances of starting the game with no sound and others where the sound was delayed, or lagged a few seconds gave way yesterday after an update to what we have now where sound in ETQW is now lagging for 10's of seconds or more, sometimes from the start of the game, sometimes after 10 minutes or so of play.  

Very unfortunate because I generally like Pulseaudio and would rather not pull it out by the roots as some have.  The bug has been filed [here.]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/577727")

The solution that finally worked for me, mostly, I found in post #6 [here]("http://swiss.ubuntuforums.org/showthread.php?p=9150130") which is:

> I ended up switching the game to using OSS ("s_driver oss" at the game console) and then running the game using pasuspender.

Its a workaround but it does get ETQW playable again.  Only problem is that now my USB mic no longer works.  I'm wondering if OSS identifies it differently than Alsa?


[SOLVED]11 May, 2011 Installed Debian Stable. All Pulseaudio issue resolved.

---

