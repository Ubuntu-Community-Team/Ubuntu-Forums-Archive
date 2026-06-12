---
title: "RealPlayer seems fine, but no sound!"
date: 2006-04-25
forum: General Help
---

### Post by jaclynL on 2006-04-25
I just installed RealPlayer 10 Gold and can't seem to find a preference allowing me to select an audio driver.  Whenever I try to listen to audio files or streaming audio, it appears to be playing fine -- buffering, counting time elapsed, etc. -- but there is no sound.  I also frequently use Quod Libet and XMMS with no trouble, so I assume I need to specify for it to work with ALSA or some such.  The only trouble is, this doesn't appear in the preferences like it does for, say, XMMS ("output plugin").

I couldn't find anything on the Helix/Real forums, so I figured I'd see if anyone here had experienced a similar issue.  Any takers?

---

### Post by Toxicity999 on 2006-04-25
Well if you can take the alternate route, find out what Realplayer defaults its sound output to and play with that driver.

Also, Welcome to the forums.

---

### Post by jaclynL on 2006-04-27
thanks :grin:

Actually, part of the problem was that I didn't have ALSA set as my default audio sink...silly me.  Now I just have an issue with no sound in Firefox or RealPlayer, which looking at the forums seems like it could be a related issue.  I haven't tried to do anything that requires sound in the browser since I switched distros (from Debian), so I didn't even realize it wasn't working.  Flash stuff works okay, but everything is silent.  I'll have to do some reading about this one :confused:

---

