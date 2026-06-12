---
title: "Odd sound problems (Ubuntu 10.10)"
date: 2011-02-18
forum: General Help
---

### Post by VxMxPx on 2011-02-18
So I'm using Ubuntu 10.10 (64bit version); and external USB sound card, by Trust.
The sound is in general ok, but sometimes there are really odd problems. Especially on Sykpe some effects (like when you receive a message) doesn't works (or they sound very scratchy). Same story with Emesene.

Funny thing is that sometimes they are almost totally ok, and sometimes I can't hear them at all. (And this ain't connected with restart or whatever - it's rather random when system is running).

The sound in Rhythmbox works perfectly fine. It's also fine in Skype (when I talk with someone) - only on one occasion was so scratchy that I couldn't hear the persons at all. (I solve that with: "sudo killall -9 pulseaudio")

-----

I don't know if is good for something, but here are settings of my alsamixer:

[ATTACH]183820[/ATTACH]

... Any idea how to fix this?

Thank you for any suggestion.

---

### Post by VxMxPx on 2011-03-22
If anyone is interested what the problem was.
*If there was two sound sources (for example skype and youtube vid.), sound got really distorted.*

So, the problem was apparently caused by *fade* setting, in "Sounds settings", when fade was set to 100% front or 100% back, the distortion appeared. The soulution for me was to keep it in the middle or to set only 90% front - just not 100%;

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186824&stc=1&d=1300818125[/IMG]

---

