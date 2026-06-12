---
title: "Arch install question about graphics driver"
date: 2009-09-27
forum: General Help
---

### Post by ninjapirate89 on 2009-09-27
Ok I am following this [http://wiki.archlinux.org/index.php/Beginners_Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide")
and I get down to Install Video Driver Package. I typed in lspci | grep VGA and here is what I get: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03). Which of these should I install?

```

    * xf86-video-apm — Alliance ProMotion video driver
    * xf86-video-ark — ark video driver
    * xf86-video-ati — ATI(AMD) video driver
          o xf86-video-r128 — ATI(AMD) video driver for X.org ati Rage128 video
          o xf86-video-mach64 — ATI(AMD) video driver for X.org mach64 video
          o xf86-video-radeonhd — open source radeonhd driver 
    * xf86-video-chips — Chips and Technologies video driver
    * xf86-video-cirrus — Cirrus Logic video driver
    * xf86-video-dummy — dummy video driver
    * xf86-video-fbdev — framebuffer video driver
    * xf86-video-glint — GLINT/Permedia video driver
    * xf86-video-i128 — Number 0 i128 video driver
    * xf86-video-i740 — Intel i740 video driver
    * xf86-video-i810 — Intel i810/i830/i9xx video drivers (deprecated - use -intel)
    * xf86-video-intel — Newer Version of Intel i810/i830/i9xx video drivers
    * xf86-video-intel-legacy — Legacy-driver for older intel cards as 82865G (xf86-video-intel currently crashes with older cards)
    * xf86-video-imstt — Integrated Micro Solutions Twin Turbo video driver
    * xf86-video-mga — mga video driver (Matrox Graphics Adapter)
    * xf86-video-neomagic — neomagic video driver
    * xf86-video-nv — Nvidia nv video driver
    * xf86-video-nouveau — Open Source 3D acceleration driver for nVidia cards (experimental), check: [1] for Current Status
    * xf86-video-openchrome — VIA/S3G UniChrome, UniChrome Pro and Chrome9 video driver
    * xf86-video-rendition — Rendition video driver
    * xf86-video-s3 — S3 video driver
    * xf86-video-s3virge — S3 Virge video driver
    * xf86-video-savage — savage video driver
    * xf86-video-siliconmotion — siliconmotion video driver
    * xf86-video-sis — SiS video driver
    * xf86-video-sisusb — SiS USB video driver
    * xf86-video-tdfx — tdfx video driver
    * xf86-video-trident — Trident video driver
    * xf86-video-tseng — tseng video driver
    * xf86-video-unichrome — VIA S3 Unichrome video drivers
    * xf86-video-v4l — v4l video driver
    * xf86-video-vesa — vesa video driver
    * xf86-video-vga — VGA 16 color video driver
    * xf86-video-vmware — vmware video driver
    * xf86-video-voodoo — voodoo video driver 

```

I know this should be in the Arch forum but I like you guys better and I know there are Arch users in here. :D

---

### Post by ninjapirate89 on 2009-09-27
Not many people seem to be on right now, so I'm going to install the driver that the tut says is the most generic and you guys can tell me how bad I messed up tomorrow :D

---

### Post by LoloftheRings on 2009-09-27
Happy arch user here, I searched the web a bit and found this:

[http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_cores_and_chipsets](http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_cores_and_chipsets)
If you look closely, you will see 915GM right below GMA 900

knowing this, you can read on this page [http://wiki.archlinux.org/index.php/Intel_Graphics](http://wiki.archlinux.org/index.php/Intel_Graphics) that you will probably need 'intel-legacy', but they do recommend trying 'intel'.

Arch wiki is just awesome, there's so much to learn on it :)

---

