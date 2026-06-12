---
title: "Compiz and Intel is it possible"
date: 2006-03-19
forum: General Help
---

### Post by FISH on 2006-03-19
Hey guys/gals i bought a new laptop and it has a Mobile Intel 915GM/ 910 GML Express Chipset family card. I haven't installed Ubuntu on it yet cause the acer manufacturer have hidden a partition where Windows xp is stored. so I wanted to make sure i don't delete it. Anywhoo. I was wondering if someone could tell me if its possible to have compiz with a intel card. If so where do you find drivers for Intel video cards, ive googled so anyhelp is appreciated. Im accustomed to using nvidia cards, so this is new for me. And yea if anyone knows if theres any guides for setting up compiz with Intel with Ubuntu.

Ty.

---

### Post by audax321 on 2006-03-19
My laptop (HP DV1000) has a Intel GMA900. I installed compiz on it using a preview version of the upcoming Dapper Drake (LiveCD). It worked, but ran rather slow hopefully just because of the LiveCD (definitely better than with plain old composite). From what I've heard, with some tweaking in xorg 7.0 which will be in Dapper the GMA900 can run pretty well. I don't plan on messing around with it until Dapper final is released though. Hope that helped a little, xorg 7.0 is supposed to have better drivers for the video card.

I believe the 910 GML uses the i810 driver as well... not sure though. It can be found on the Intel site, but is included with Ubuntu anyway. If you wait for Dapper, it *should* have the latest in it.

Here are some links I found for compiz and intel:

[http://ubuntuforums.org/showthread.php?t=134069&highlight=compiz+intel](http://ubuntuforums.org/showthread.php?t=134069&highlight=compiz+intel)
[http://ubuntuforums.org/showthread.php?t=145536&highlight=compiz+intel](http://ubuntuforums.org/showthread.php?t=145536&highlight=compiz+intel)

Basically, the Intel drivers need to mature a little more and XGL just plain isn't optimized for Intel yet... hopefully will be in the future though.

---

