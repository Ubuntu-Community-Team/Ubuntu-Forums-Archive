---
title: "Sound Issues Ubuntu 10.10"
date: 2011-03-06
forum: General Help
---

### Post by alpha_zeeno on 2011-03-06
I'm an Ubuntu newbie here, and I recently bought an ASUS N53JF-XE1 laptop, and after a new installation of Ubuntu 10.10, I don't seem to be able to get the sound working (neither from speakers, nor from headphones).

I've been searching a lot of places, and with no luck and a lot of frustration, I'm coming here for a possible solution!

According to "lspci -v", this is the info for my sound card:


```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: ASUSTeK Computer Inc. Device 1113
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at d9c00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

Using "aplay -l" gives me this:

```
aplay: device_list:235: no soundcards found...
```

It seems to me that I'm somehow missing the drivers for my sound card. However, I don't know where to find the correct drivers or how to install them. I've been all over the alsa-project website, and I can't find anything useful.

Any help would be really useful. :(

---

### Post by MASHAVELLI on 2011-03-20
I am also having the same problem, it is really driving me insane!! I have tried almost everything.
Some one please advise if there is anything besides reinstalling... this is such a frustrating problem.

---

### Post by Script Warlock on 2011-03-20
check this link it might help [http://ubuntuforums.org/showthread.php?t=1481792&page=2](http://ubuntuforums.org/showthread.php?t=1481792&page=2)

---

