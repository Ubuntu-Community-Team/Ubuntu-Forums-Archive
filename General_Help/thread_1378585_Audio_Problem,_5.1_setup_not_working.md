---
title: "Audio Problem, 5.1 setup not working"
date: 2010-01-11
forum: General Help
---

### Post by sensay on 2010-01-11
I recently changed my motherboard over in my main desktop, everything is working great except im having some very bizarre audio problems.

Im using a 5.1 speaker system but not all my speakers play sound. I have tested the obvious. Alsamixer has all levels at maximum, i edited the daemon.conf file in /etc/pulse so that it was set to 6 channel and not 2.

When i run speaker-test -Dplug:surround51 -c6 -twav i get sound on all speakers apart from REAR RIGHT and REAR LEFT. However, what makes things really confusing is that if i attempt to play any 5.1 audio through VLC player the only speaker that does not give correct sound is FRONT CENTER. RR and RL work as they should!

In my windows boot the 5.1 setup functions as it should. Worth noting though, my old motherboard had an audio interface with 6 ports at the back (three of which were assigned by default as center, rear and front ports) and my current audio interface only has 3 ports. I had to use the audio driver software in windows to assign the mic port and line in port as the additional 5.1 ports, is something similar to this required in linux?

Hope someone can help!

---

### Post by sensay on 2010-01-12
BUMP!

Come on guys, hardly seems like a problem that would stump you all!

---

