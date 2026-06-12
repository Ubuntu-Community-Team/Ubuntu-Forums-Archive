---
title: "Screen resolution not fitting monitor"
date: 2012-08-19
forum: General Help
---

### Post by adc90 on 2012-08-19
Sorry if this is posted in the wrong section or anything. I recently put Ubuntu on an old desktop I'm messing with and I can't seem to get a screen resolution that displays everything without cutting anything off. What I'd like to be able to do is run it at a resolution of 1680x1050 however the display panel only gives me the options of (1024x760)and (800x600) neither of which display the entire desktop. I ran the following command 'lspci -nn l grep VGA' to get the chip set and came up with the following:

00:02.0 VGA compatible controller [0300]: Intel Corporation  82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562]  (rev 03)
clevenger_1@Render1:~$ 

My question is basically do I need to install a new driver in order to get it to work and if so how would I go about doing it, or am I just missing something here (I am pretty new to Ubuntu :P)

---

### Post by raja.genupula on 2012-08-19
have you opened Monitor settings in System settings ? there you can choose the resolution you want from the available options .

If that wont help try with xrandr .[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by adc90 on 2012-08-19
> **raja.genupula said:**
> have you opened Monitor settings in System settings ? there you can choose the resolution you want from the available options .

If that wont help try with xrandr .[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

yeah I messed with the resolution under system settings and the only additional option I seemed to get from the 'xrandr' command was  a resolution in between (1024 x 768) and (800 x 600). The panning might help straighten out the screen though I think I might need a driver to enable the correct resolution. The closest thing I've found though to getting the driver is [this]("http://ubuntuforums.org/showthread.php?t=1846023") thread, though I have no idea how to compile a driver or what that includes doing :P

---

