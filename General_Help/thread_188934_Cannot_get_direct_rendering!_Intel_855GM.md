---
title: "Cannot get direct rendering?! Intel 855GM"
date: 2006-06-04
forum: General Help
---

### Post by E1000 on 2006-06-04
I am trying to use Xgl so I can use compiz, but I cannot get direct rendering to work.

When 0=standard in the gdm.conf, I have direct rendering and can play tuxracer, but when 0=Xgl, It is set to mesa indirect render... what could be my problem?
Xgl and compiz were installed via apt-get; I did not compile from source.


here's the relevant parts of my xorg.conf
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option          "NoAccel"       "false" # I have tried with these both
	Option 		"DRI" 		"true"    # enabled and commented out
                                                        # the result is the same
EndSection

Section "DRI"
	Mode	0666
EndSection

```

any hints or suggestions? 
Thanks in advance
-Evan

---

