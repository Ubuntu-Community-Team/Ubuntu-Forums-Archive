---
title: "xmms only plays one song, wont continue to next track?"
date: 2010-10-03
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-03
I just spent a lot of time getting XMMS to work with a nice skin and now it can't even do the most basic thing, proceed to next track once the current track is finished.

I looked around the net and the recommendations i got were to change the output plugin from ALSA to OCC - but then my sound wont work. Tried the other output plugins too, no difference, some caused other issues.

Another recommendation i got was to uncheck NO PLAYLIST ADVANCE. I did that too and the problem still continued.

Anyone have any ideas? It would be really great if someone could help me out as this is the closest winamp like player i have come across.

---

### Post by MaquinaX on 2011-12-04
Hello all,
           Having the same issue, and found my answer here:
[http://arstechnica.com/civis/viewtopic.php?f=16&t=904450](http://arstechnica.com/civis/viewtopic.php?f=16&t=904450)

Appears that for some reason, the .xmms config is set to some values, which
do not correspond the actual preferences indicated on the GUI, so in the case of "NO foward Advance", you have to enable it, and then re-disable.


MaquinaX

---

