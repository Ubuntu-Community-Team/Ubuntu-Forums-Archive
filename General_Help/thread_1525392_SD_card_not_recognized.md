---
title: "SD card not recognized"
date: 2010-07-06
forum: General Help
---

### Post by am529 on 2010-07-06
I am using a case from a eMachines T3104 computer (though all the hardware has been replaced except the optical drive) and on the front it has a 8-in-1 media card reader (which also includes a USB port). The USB port works fine, but when I put in a SD card (technically a microSD card with an adapter) the light comes on but it doesn't show up in Ubuntu (I'm running version 10.04). I know my card reader *can* read them because I was able to use them in Windows XP (though that was before I rebuilt my computer).

Does anyone know what I have to do to be able to access it?



I saw a similar thread, so I figured I'd post the output of lsusb and dmesg (well part of it anyway).

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1241:1177 Belkin F8E842-DL Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````

[15021.124080] usb 5-3: reset full speed USB device using ohci_hcd and address 2
[15031.420142] usb 5-3: reset full speed USB device using ohci_hcd and address 2
[15047.720112] usb 5-3: reset full speed USB device using ohci_hcd and address 2
[15048.024090] usb 5-3: reset full speed USB device using ohci_hcd and address 2
[15058.320086] usb 5-3: reset full speed USB device using ohci_hcd and address 2
[15058.483063] sd 6:0:0:0: Device offlined - not ready after error recovery

```

---

### Post by LowSky on 2010-07-06
looks like the SD card is corrupted or wasn't unmounted correctly from its last device. Or it could be the SD card is actually a SDHC, and the card reader cannot read the format. Older card readers have problems with the higher capacity SD cards (4+ GB)

---

### Post by am529 on 2010-07-06
> **LowSky said:**
> ...Or it could be the SD card is actually a SDHC, and the card reader cannot read the format.

Yeah, shortly after I posted I realized that I had a microSDHC and I don't think those were even around when my card reader was made.

---

### Post by cominatyalive on 2012-05-07
If it's anything like I experienced, I have an answer that fixed what I had going on. I put my Sans Disk Compact Flash card into my reader of my HP All In One Printer and nothing. It used to work before. Not even recognized by my computer. I also noticed that even my Printer drive was not detected in (My Computer) in Zorin 11.04 Natty. Therefore I Turned my Computer off, Unplugged my USB cord of my Printer from the computer and turned off my printer. I then turned my computer back on, wait for everything to load, I plugged my printer's USB cord back into my computer, then turned my Printer back on. Right away everything was detected. My printer also is now showing up as a drive in (my Computer). The reason my printer is displayed as a drive, is because it has the reader slots built into my printer. Which is a valid drive and should be detected on your computer, under (My Computer) folder. This also holds true to built in Flash card readers built into your PC or external readers alike. I hope this helps many of you out there. This is not only for Ubuntu 11.04, but all computers. Windows or Linux. Cheers!

---

### Post by sffvba[e0rt on 2012-05-08
Thanks for the additional input.

*Old thread **closed**.*


404

---

