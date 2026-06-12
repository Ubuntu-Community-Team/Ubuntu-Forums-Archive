---
title: "Rhythmbox won't detect MP3 player"
date: 2010-04-16
forum: General Help
---

### Post by sideaway on 2010-04-16
Hey there guys, I have a Toshiba Gigabeat F60 that I can't get to detect with Rhythmbox. I have libmtp and mtp-detect installed and the plugin 'Portable Players - MTP' is enable in Rhythmbox. Using mtp-detect gives this error;

```
libmtp version: 1.0.2

Listing raw device(s)
Device 0 (VID=0930 and PID=0009) is a Toshiba Gigabeat MEGF-40.
   Found 1 device(s):
   Toshiba: Gigabeat MEGF-40 (0930:0009) @ bus 2, dev 6
Attempting to connect device(s)
LIBMTP PANIC: Unable to find interface & endpoints of device
Unable to open raw device 0
OK.

```

Rhythmbox gives this error.

```
Media player device error
Unable to open the Toshiba Gigabeat MEGF-40 device

```

Can anyone help?

I'm currently using 10.04, but the issues was in 9.10 as well, I updated thinking It may fix something.

---

### Post by sideaway on 2010-04-16
Ok, just plugged it into a Vista box and Windows Media Player 11  doesn't detect it either. Also it shows up with the other Hard Drives, where as most show up under removeable drives or something similar... is this an issue?

---

### Post by Chronon on 2010-04-16
Sorry, I just drag and drop (in MSC mode) to sync files to my Gigabeat.

---

### Post by sideaway on 2010-04-16
how do I change modes etc? I've got rockbox installed so just drag and drop anyway...

---

### Post by Chronon on 2010-04-16
If you have Rockbox installed then it should be MSC already, which probably explains why Rhythmbox isn't detecting it as an MTP device.

---

### Post by sideaway on 2010-04-16
Oooh, so I can't use it as a MTP device while RB is installed? I know very little about these modes :P

---

### Post by Chronon on 2010-04-16
Rockbox's USB mode is MSC only*.  If you boot into the Toshiba firmware you can set the USB controller to MTP mode (unfortunately, there isn't a convenient way to dual boot Rockbox and the Toshiba firmware at this time).  I prefer to have access to my Gigabeat as a storage device so I would rather have it in MSC mode anyway.

* Actually, Rockbox allows HID functionality as well but this is beside the point here.

---

### Post by sideaway on 2010-04-16
What exactly would rockbox use HID for? I thought it stood for Human Interaction Device, so input devices such as a mouse or keyboards.

---

### Post by Chronon on 2010-04-16
Actually, HID functionality is provided through the software USB stack, which isn't used on players that have a hardware controller (like the Gigabeat F40).  Sorry for the irrelevant information.

On PortalPlayer based players (which tend to not have a hardware controller) USB connection allows simultaneous access as a storage device and an input device.  It can be used to control a slideshow or an audio player application, for example.

If you want help or detailed info regarding Rockbox it's probably best to go to the Rockbox forums.

---

