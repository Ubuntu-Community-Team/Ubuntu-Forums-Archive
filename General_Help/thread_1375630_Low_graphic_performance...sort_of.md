---
title: "Low graphic performance...sort of"
date: 2010-01-08
forum: General Help
---

### Post by Another Monkey on 2010-01-08
I dropped 9.10 on to my g/f's laptop last night (Compaq Presario B1015).  Pentium CPU (3ghz), 512meg, Nvidia gaphics card (GeForce FX Go5200).

Not long after install it offered me the Nvidia proprietary drivers (version 173 and 96), I installed version 173.  I then let it fully update.

After reboot, compiz etc work and the benchmark showed around 330fps which seemed good (another laptop I have with an ATI Radeon reports around 120fps).  As a final test I ran Extreme Tux Racer and that struggled to get over 4fps.

Any idea what I could have done wrong or what I need to tweak?  I know 512mb is not a lot of RAM, but the graphics cards is decent enough for an old lappy and I would have expected better performance.

Thanks.

---

### Post by gsmanners on 2010-01-08
Many 3D games depend on the CPU speed (especially when the video card is a low end) which in your case I would guess is pretty slow.

---

### Post by NoaHall on 2010-01-08
Try turning compiz off, then running the game.

---

### Post by Another Monkey on 2010-01-08
Face-Palm.

Yeah, disabling Compiz made a huge difference.  ETR fps jumped to 85-ish.

Well, OK.  I guess that shows me how to get hi performance, but I am not clear on why Compiz would cause such a performance degradation...guess it's time to do some digging...

Thanks.

---

### Post by NoaHall on 2010-01-08
> **Another Monkey said:**
> Face-Palm.

Yeah, disabling Compiz made a huge difference.  ETR fps jumped to 85-ish.

Well, OK.  I guess that shows me how to get hi performance, but I am not clear on why Compiz would cause such a performance degradation...guess it's time to do some digging...

Thanks.

:)
Compiz is quite resource taking, especially on the older nvidia cards.

---

### Post by Another Monkey on 2010-01-08
Obviously!  But as Compiz is not "active" as such when ETR is running, I would not have expected the degradation to be so much.

Live and learn I guess.

---

