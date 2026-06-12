---
title: "Googleearth 6 and Ubuntu 10.10 rendering"
date: 2011-01-07
forum: General Help
---

### Post by petermck on 2011-01-07
Hi,
I've got GE 6 working on Ubuntu 10.10, but there is a problem with the rendering. Images have jagged edges and there are streaks of colour pointing toward the centre of the image.
The problem is worse if I go into Tools/Options/3D View and uncheck "Show terrain".
I've tried turning off 3D desktop effects, using safe mode (in GE) and various other changes in the GE 3D view options without success.
I'm using a Gigabyte motherboard with an integrated radeon 2100 GPU and the ATI open source drivers. I don't seem to be able to get the fglrx driver installed and working with this chip, so I have not been able to test this config.

---

### Post by dcstar on 2011-01-07
> **petermck said:**
> Hi,
I've got GE 6 working on Ubuntu 10.10, but there is a problem with the rendering. Images have jagged edges and there are streaks of colour pointing toward the centre of the image.
The problem is worse if I go into Tools/Options/3D View and uncheck "Show terrain".
I've tried turning off 3D desktop effects, using safe mode (in GE) and various other changes in the GE 3D view options without success.
I'm using a Gigabyte motherboard with an integrated radeon 2100 GPU and the ATI open source drivers. I don't seem to be able to get the fglrx driver installed and working with this chip, so I have not been able to test this config.

This might help:

[http://ubuntuforums.org/showthread.php?t=936999](http://ubuntuforums.org/showthread.php?t=936999)

---

### Post by petermck on 2011-01-09
Hi,
Thanks for the suggestion, but unfortunately I can't use the ATI proprietry drivers with this GPU on Maverick or Lucid. According to the Unofficial AMD Linux Community Wiki [Ubuntu Maverick Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx"), ATI do not support later kernels on legacy cards.
That's a bit of a bummer since I only just purchased this motherboard new and was told nothing about it being an old model. To be fair, I have had very few problems, in fact only this one with Google Earth, which is not bad. Everything else appears to work seemlessly on Lucid and Maverick, which is a pretty good testament to how far Ubuntu has come.
It appears the problem may be with the open source drivers.

---

