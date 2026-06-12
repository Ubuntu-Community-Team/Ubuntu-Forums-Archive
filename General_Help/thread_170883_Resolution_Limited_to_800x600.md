---
title: "Resolution Limited to 800x600"
date: 2006-05-05
forum: General Help
---

### Post by mb2k on 2006-05-05
Dear,

i have recently installed ubuntu new to my server, and it does not matter which Resolutions i set in the xorg.conf, the only 2 option which i can choose in the Gnome Resolution Menu are 640x480 and 800x600.
Even when only 1024x768 is in the xorg.conf i can not choos it -..-

I`m really getting annoyed about this ...

my screen is a 15" LCD which can easily do 1024x768 and the Matrox G400 can do the same ....

many thanks for any help :-({|=

---

### Post by mschievano on 2006-05-05
[QUOTE=mb2k]Dear,

i have recently installed ubuntu new to my server, and it does not matter which Resolutions i set in the xorg.conf, the only 2 option which i can choose in the Gnome Resolution Menu are 640x480 and 800x600.
Even when only 1024x768 is in the xorg.conf i can not choos it -..-

I`m really getting annoyed about this ...

my screen is a 15" LCD which can easily do 1024x768 and the Matrox G400 can do the same ....

many thanks for any help :-({|=[/QUOTE]

set the resolution of the monitor in xorg.conf.

for me (17"):

```

Section "Monitor"
	Identifier	"L17AX"
	Option		"DPMS"
	HorizSync	50-80
	VertRefresh	50-75
EndSection

```

and then look at 
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"L17AX"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

```

---

### Post by mb2k on 2006-05-05
I did exactly this, but whaterever i write in xorg.conf, I only get Resolution to choose up to 800x600.

I have never seen something stupid like this ....

the xorg.conf under /etc/X11 is the only config file on my system ... it seems like gdm or gnome is using his own settings an ignoring the resolution section in my xorg.conf ...

---

### Post by mb2k on 2006-05-06
Does nobody have a clue ???

I have now installed Debian from Scratch and its the same thing ...

Very strange ,.... :(

---

