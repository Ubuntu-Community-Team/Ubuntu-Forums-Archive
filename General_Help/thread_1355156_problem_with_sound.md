---
title: "problem with sound"
date: 2009-12-14
forum: General Help
---

### Post by .ringaila on 2009-12-14
I installed Ubuntu 9.10, when I connect the headphones my speakers doesn't turn off. I've been reading forums for hours but nothing helped. I have Asus f3ka, the sound card: ALC660VD.
ALC861VD/660VD
          3stack 3-jack
          3stack-dig 3-jack with SPDIF OUT
          6stack-dig 6-jack with SPDIF OUT
          3stack-660 3-jack (for ALC660VD)
          3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
          lenovo Lenovo 3000 C200
          dallas Dallas laptops
          hp HP TX1000
          auto auto-config reading BIOS (default)

tried all lines in /etc/modprobe.d/alsa-base,
any suggestions. ? :?:

---

### Post by Royke on 2009-12-14
Hello .ringaila,
I have the same problem here. But when i stop the pulseaudioserver it works like before! The command is: killall pulseaudio  
Let's hope the devellopers read this too ;)

---

### Post by .ringaila on 2009-12-15
unfortunately this doesn't work for me...

---

