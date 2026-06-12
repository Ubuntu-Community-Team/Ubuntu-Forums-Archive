---
title: "Ubuntu doesn't recognize onboard Realtek HD"
date: 2012-05-08
forum: General Help
---

### Post by DJZephyr on 2012-05-08
First off, since I know this'll be needed, some info on my hardware.  I can put in a 'lshw' readout if need be, but since I'd rather not start off with a wall o' text, I'll keep it simple-

AMD Athlon X2 4200+ dual-core- 2.2ghz per core, MSI K9VGM-V motherboard
MSI GeForce 9400 GT- 550mhz core, 512mb VRAM
2gb DDR RAM, dual 17" monitors (one Acer panel, one KDS boat anchor)
Windows 7 Home Premium, DirectX 11, onboard Realtek HD w/ Logitech X530 speaker set, Logitech G110 keyboard

So I decided I'd do a bit of dual-boot experimentation and give Ubuntu 12.04 a try.  Right now, my biggest issue is getting sound to work- the OS seems to recognize my Logitech keyboard's lil audio setup (basically a USB PnP device meant for headsets), but not my motherboard's built-in Realtek HD audio (through which my Logitech 5.1 speaker set is connected).

I've downloaded the Linux drivers from the Realtek site (extracted the folder, ran the install script), and have tried to figure out ALSA (completely baffled here).  Now, I'm pretty good with computers, but I'm a Windows veteran, and am completely unfamiliar with Linux, so half the time I've no idea what the readmes are talking about.  So any plain-English help would be VERY welcome.

---

### Post by xyzzyman on 2012-05-08
That particular Realtek chipset is supported already so no need to start messing with installing a replacement ALSA driver. Most likely things aren't being routed right. To give us a better idea of your systems settings visit:

[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

And follow the directions and post back here with the link to the result.

---

### Post by DJZephyr on 2012-05-10
Mmk, here it is-

[http://www.alsa-project.org/db/?f=852c3e03e09e8bde11d566cf7275f9ce8cfabf2a](http://www.alsa-project.org/db/?f=852c3e03e09e8bde11d566cf7275f9ce8cfabf2a)

In the meantime, I dug up an old pair of Yamaha speakers and plugged em in to my keyboard's audio port.  Bit of a jury rig, but better than headphones.

---

### Post by xyzzyman on 2012-05-10
It recognizes your onboard realtek card, but you are getting a crash... It's hard to say because you've tried to overwrite the default drivers. Does sound work when you boot off a Live CD/USB of Ubuntu and don't have the usb audio device plugged in?

---

### Post by DJZephyr on 2012-05-11
Gonna be hard to test that theory.  First, the PnP sound device is built in to my keyboard; I might be able to scrounge up an old one in the garage tho.

But that's only if I can figure out why my computer refuses to boot to my thumb drive... I've got it set up to do so in the BIOS (USB-FDD set above hard drives), but it seems to ignore the thumb drive and go straight to the dual-boot prompt.

Things just keep getting weirder...

---

