---
title: "VLC doesn't recognise the sound card"
date: 2009-07-14
forum: General Help
---

### Post by nsblenin on 2009-07-14
I've just installed VLC but there is not sound in the sound blaster card (PCI) but when I connect in the jack output of the mainboard then it sounds.

I selected in options of sound in ubuntu in SBLIVE. totem and other programs work with the SB card but VLC only with mainboard soundcard.

I tried all combinations in options of VLC. I think that VLC doesn't know that there is another sound card.

How can I configure VLC in order to use the SB card instead of mainboard soundcard?
Thanks

---

### Post by nsblenin on 2009-07-14
Finilly I found the solution!!!!!!!!!!!. I opened options in VLC and I switched to Show setting: ALL

AUDIO -> OUTPUT -> ALSA ->REFRESH LIST -> and then in the list I could find my SBLIVE 5.1 sound card

---

