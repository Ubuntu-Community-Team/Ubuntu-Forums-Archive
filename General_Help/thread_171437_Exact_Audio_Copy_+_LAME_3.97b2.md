---
title: "Exact Audio Copy + LAME 3.97b2"
date: 2006-05-06
forum: General Help
---

### Post by Onyros on 2006-05-06
Hi there, guys ;)
I'm an Ubuntu noob (2 months into Linux, as well), and I've already converted completely. I've gotten rid of XP ever since I found Ubuntu.

I was quite the XP geek, knew my way around pretty well, and I am in the process of (always) learning new things about Linux in general, about Ubuntu in particular.

I've set up Exact Audio Copy, as I was a little unsatisfied with both Goobox and Sound Juicer. I used WINE, obviously, with LAME's recommended version (Hydrogenaudio) --> 3.97b2.

I also used the setting
```
-V 2 --vbr-new --id3v2-only --pad-id3v2 --ta "%a" --tt "%t" --tl "%g" --ty "%y" --tn "%n" %s %d
``` which is supposed to correspond to alt preset standard.

I just converted Pearl Jam's last album to mp3, using that very config, but results are somewhat strange, but not in terms of quality. Files are just getting bigger than I had expected.

With that setting, for example, the first song "Life Wasted", gave a 234kbps VBR file, whereas with CDex and LAME 3.96.1 (my wife's laptop, with XP still in dual boot) she got a 214kbps file (with alt preset standard).

Has anyone converted the album using the same settings, or can someone please just compare results with me? I'm finding a difference of 20kbps between 3.97b2 and 3.96.1 a little too strange ;)

---

