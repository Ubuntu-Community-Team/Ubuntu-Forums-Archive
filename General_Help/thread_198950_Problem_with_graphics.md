---
title: "Problem with graphics"
date: 2006-06-18
forum: General Help
---

### Post by Hoffmann on 2006-06-18
When I try to lounch some programs I get the error:

> X server has no OpenGL GLX extension.
Try a different display or try enabling GLX in your X Server
...
WARNING X server has no OpenGL GLX extension.
WARNING Try a different display or try enabling GLX in your X Server
How could I fix this? Is this related to nvidia-glx?

---

### Post by mlind on 2006-06-18
For NVidia, do you have 

```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
**#	Load	"dri"**
	Load	"extmod"
	Load	"freetype"
	**Load	"glx"**
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

```

on /etc/X11/xorg.conf (bolded parts) and nvidia-glx package installed ?

---

### Post by Hoffmann on 2006-06-18
[QUOTE=mlind]For NVidia, do you have 

```

Section "Module"
	Load	"bitmap"
	Load	"ddc"
**#	Load	"dri"**
	Load	"extmod"
	Load	"freetype"
	**Load	"glx"**
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

```

on /etc/X11/xorg.conf (bolded parts) and nvidia-glx package installed ?[/QUOTE]

What I have is:

> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
and nvidia-glx package is installed.
What do you think?

---

### Post by mlind on 2006-06-18
[QUOTE=Hoffmann]What do you think?[/QUOTE]

Looks fine to me, as long as glx is there and dri isn't. If you have nvidia-glx package
installed and "nvidia" as Driver on Device section, then I'm out of ideas..

Check our /var/log/Xorg.0.log that GLX extension is properly loaded by nvidia driver.

---

### Post by Hoffmann on 2006-06-18
[QUOTE=mlind]Looks fine to me, as long as glx is there and dri isn't. If you have nvidia-glx package
installed and "nvidia" as Driver on Device section, then I'm out of ideas..

Check our /var/log/Xorg.0.log that GLX extension is properly loaded by nvidia driver.[/QUOTE]
I solved my problem.
I my case, I should not to install nvidia-glx. So, I decided to re-install ubuntu, and I didn't installed nvidia-glx. All is fine now.
Many thanks!;)

---

