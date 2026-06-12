---
title: "ATI Card woes..."
date: 2011-11-16
forum: General Help
---

### Post by lostsoul1313 on 2011-11-16
So we all know that radeon pretty much doesn't support linux worth a damn.

I run a dual-boot environment with windows 7 and linux (ubuntu, arch, elive, etc. depends on how I'm feeling)

So I have a radeon hd 6970, at stock because I got unlucky, this card doesn't like overclocking AT ALL. I'm thinking of trading it for a GTX 470 (560/570 if someone else offers one of those)

what I wanna know is, should I do this?

currently my CPU is holding my card back heavily anyway, I have athlon II 3 cores OC at about 3.6 ghz, so would I notice the performance drop? I figure if my luck increases any I could OC the 470 almost on par with the 570 settings, but it would still be lower than my 6970 OC or not. what're your opinions on this?

---

### Post by Mark Phelps on 2011-11-16
Unfortunately, Ubuntu continues to have problems with AMD restricted drivers.  I have onboard ATI and the drivers were so bad, I removed them and went back to the open source drivers.

I've read that with Catalyst 11.11 (which just came out), they have finally fixed the problems and the drivers work now.  But I have not had a change to check this out.

You can do a search in the Video subforum to see what folks have posted there.

But, you probably would get more detailed info if you jumped over to the Phoronix forums.  They do a lot of hands-on testing with AMD/ATI stuff and may have updates on the driver problems.

---

### Post by Linuxisfast on 2011-11-16
Have ATI Radeon 6250 on my netbook which uses AMD C50 CPU, I have no issues whatsoever with the regular and not post release drivers.

---

### Post by marinara on 2011-11-17
which application are you using the card for?

I can't overclock my card anyhow... it tends to overheat.  Just ignore the opportunity to overclock

---

### Post by lostsoul1313 on 2011-11-17
Thanks for the responses, I decided to just ignore linux for now until they do something about supporting the 6900 cards, it has graphical glitches in most desktop environments (it likes gnome 2, kde, and enlightenment for the most part though) and windows dragging is painfully slow, with vsync off and everything.

open source drivers seem to be more compatible, but with those drivers my snes9x and my pcsxr lag (they don't with proprietary) which is a nice time killer when I get a little bored.

I gave up because yesterday I was running Bhodi, and everything was perfect, I had the excited face and everything. and today it broke when testing out the different graphic profiles >.>

---

### Post by Mark Rooney on 2011-11-19
> **Linuxisfast said:**
> Have ATI Radeon 6250 on my netbook which uses AMD C50 CPU, I have no issues whatsoever with the regular and not post release drivers.

I also had no issues with the same configuration and 11.04.

Updated to 11.10  and catalyst 11.8 when it was released with no issues however two weeks ago fglrx updated to version 8.881 and ever since compiz and unity run VERY slow. I've had to default to a Unity 2D desktop just to be able to use the netbook.

Considering an update to catalyst 11.11 as early reports suggest it fixes a lot of issues with APU's

---

