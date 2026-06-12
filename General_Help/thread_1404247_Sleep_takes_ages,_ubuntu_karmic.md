---
title: "Sleep takes ages, ubuntu karmic"
date: 2010-02-11
forum: General Help
---

### Post by gabrielcik on 2010-02-11
Hola!

I notice several issues related suspend with Ubuntu 9.10 on my Vaio W.

1. While I unplug the AC the netbook suspend
(solved changing the lid parameter to black screen)

Now when i plug - unplug the screen became black (as if i close the lid)

2 The main for me, It takes ages to suspend, the screen became immediately black but after before it really suspend pass about 1 minute!!! (it is a lot of time if u think my vaio boot very quickly).

My configuration is: Vaio W12 modified with 2 gb of ram and a OCZ Solid 2 ssd 30gb.
(only 1 partition ext2 without swap)

Thank you:)

---

### Post by ibuclaw on 2010-02-11
Does it take a minute if you run:
```
sudo pm-suspend
```
in a terminal?

Regards
Iain

---

### Post by gabrielcik on 2010-02-11
I did it... but same result.
With the difference that the screen didn't became black at the beginning but just the system stopped to respond until it really suspended.

Thx

P.s.
The resume procedure is fine, just few seconds.

---

