---
title: "HOWTO: Use USB Audio as primary and only device"
date: 2010-10-26
forum: General Help
---

### Post by Paloseco on 2010-10-26
If you want to use some USB Audio device you find out that the system sets as first device the integrated audio in the motherboard, and you always have to reconfigure the system to use the USB Audio, for example with wine. 

The best way to use always USB Audio is to disable permanently the integrated audio:

1) Find what module is the one corresponding to the integrated audio, for example for an HDA Intel High definition Audio it is called **snd_hda_intel**
You can find all loaded modules using:
**# lsmod**

2) Find the appropriate modules (if loaded) and blacklist them in /etc/modprobe.d/blacklist

Edit that file as root and add to it a line for each module you want to blacklist such as:
```
blacklist snd_hda_intel
```

3) Reboot the computer to see.

For more information about blacklisting modules read here:
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)


NOTES:

* This tutorial will not work if your USB sound card and your onboard sound card have the same chipset. I have bough a very cheap usb generic sound card and works ok:
[CENTER]
[IMG]http://i54.tinypic.com/2z5ro7c.jpg[/IMG][/CENTER]

* If the BIOS allows you to disable the onboard sound card you should try first it.

* If you set the USB audio as primary device in KDE or Control panel or such, some programs like WINE or non-desktop related will still try to use the onboard device, or if you reboot the operating system with the USB unplugged it will return the onboard audio to the default sound device, so in these cases the blacklist workaround works like a charm.

---

