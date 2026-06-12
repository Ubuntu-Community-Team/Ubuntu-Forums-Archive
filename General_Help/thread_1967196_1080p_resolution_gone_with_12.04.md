---
title: "1080p resolution gone with 12.04"
date: 2012-04-27
forum: General Help
---

### Post by viniciuscarvalho on 2012-04-27
Hi, I've installed the 12.04 release and now, my display (27" external asus on HDMI) is not working with 1080p as it was before.
The maximum resolution is 1600x900 (maximum of my notebook).

I have a radeon HD 4650, and I do have fglr installed and working.

Xorg:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual 3520 1080
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Any ideas please?

---

