---
title: "Lenovo R61i 1680 x 1050 Resolution - how?"
date: 2009-08-09
forum: General Help
---

### Post by kentcb on 2009-08-09
Hi,

I have a Lenovo R61i laptop. The highest resolution that System/Preferences/Display lists is 1280 x 800. However, this resolution doesn't have the clarity I'd expect. I noticed when booting my work machine into Ubuntu it defaults to 1680 x 1050 and looks much nicer. However, my R61i does not list that option.

I've done some googling on this subject and ended up more confused than enlightened. Are there any easy to follow steps I can take to check whether my laptop even supports 1680 x 1050 and try switching it to that resolution?

My xorg.conf looks really bare:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Thanks

---

### Post by kentcb on 2009-08-09
According to the Lenovo website, I could have either of these screens:

```
15.4-inch WXGA TFT (1280 x 800 resolution) TFT display
15.4-inch WSXGA+ (1680x1050 resolution) TFT display

```

Should I just assume that I have the WXGA and stick with my current resolution? Is there an easy way for me to check whether I have the WSXGA+?

Thanks

---

