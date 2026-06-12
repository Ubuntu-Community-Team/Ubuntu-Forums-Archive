---
title: "HDMI out"
date: 2010-08-05
forum: General Help
---

### Post by thezood on 2010-08-05
I'm having problems with HDMI out on my computer. I'm trying to connect my 40" LCD TV with HDMI. Ubuntu detects the monitor (as a 7" display) but there's no image. I know I have gotten it to work before, using proprietary ATI drivers but I prefer the open source drivers since they eliminate video tearing with KMS enabled. 

Ideas, anyone?

Computer: Toshiba Satellite L450D
Graphics chipset: ATI Radeon HD 3200
OS: Lucid 32bit

---

### Post by bprins on 2010-08-07
not meaning to offend you, but you did press the fn f5 button?

otherwise throw more data in a reply (aplay -l, lspci | grep vga, etc)

---

### Post by thezood on 2010-08-07
> **bprins said:**
> not meaning to offend you, but you did press the fn f5 button?

otherwise throw more data in a reply (aplay -l, lspci | grep vga, etc)

Isn't FN-F5 just a keyboard shortcut? It shouldn't matter if you use the display manager or the keyboard shortcut, should it?  Anyway, it doesn't work. Also tried setting a resolution with xrandr and it works in the sense that it doesn't give any error message but there's no image on the TV. It's detected by Ubuntu and shows up in the display manager.

There is picture when I boot the computer, up until Ubuntu starts, then the screen turns blue as if there's no signal. 

```

$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: ALC272 Analog [ALC272 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 1: HDMI [HDA ATI HDMI], enhet 3: ATI HDMI [ATI HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

```

---

### Post by thezood on 2010-08-09
I tried Maverick today and got picture on my LCD TV within a second of connecting the HDMI so it seems this is fixed upstream. :)

---

### Post by bprins on 2010-08-09
:P jippie kai jee!

nice have fun using it!

---

