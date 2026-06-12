---
title: "NVidia GTS250 - oddity"
date: 2010-02-25
forum: General Help
---

### Post by cryptotheslow on 2010-02-25
Hi,

Just installed a new Zotac NVidia GeForce GTS250 into my karmic system - all went smoothly as I already had the 190.53 drivers installed.

However I noticed an oddity:

Card specs are listed as:
512MB DDR3
738MHz Core Clock
2200MHz Memory Clock

In the PowerMizer section of the NVidia X Server Settings it reports the Core Clock as 740MHz and the Memory Clock at only 1100MHz.

And it's not that it has stepped down the memory clock as I'm not doing anything demanding... that is the only Performance Level listed at the bottom.

[IMG]http://www.manicradio.net/images/gt/nvid.png[/IMG]

Is this a driver issue or a card issue or something else entirely issue?

Thanks
~crypto~

---

### Post by kooldino on 2010-02-25
2200/2=1100Mhz
Maybe it's 1100Mhz because of how it calculates things with DDR or something?

---

### Post by cryptotheslow on 2010-02-25
That would kind make sense if it used DDR2 memory but it has DDR3....  so 2200/3 no ?

It seems to be working fine and I'm getting good fps in games - just trying to work out if this is some weird displayed info oddity or a genuinely knobbled card before I kick it back to the suppliers :)

---

### Post by cryptotheslow on 2010-02-26
Anyone any other ideas?

---

### Post by cryptotheslow on 2010-02-26
All cleared up now.

1100MHz actual clock, 2200MHz effective clock with DDR - kooldino was right

---

### Post by kooldino on 2010-02-26
yay

---

