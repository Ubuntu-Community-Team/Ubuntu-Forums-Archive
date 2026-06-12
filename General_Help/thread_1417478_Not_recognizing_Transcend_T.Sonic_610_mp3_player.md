---
title: "Not recognizing Transcend T.Sonic 610 mp3 player"
date: 2010-02-27
forum: General Help
---

### Post by KarthikPH on 2010-02-27
Hi, I plugged in my T.Sonic 610 mp3 player, through usb. but ubuntu is not able to recognize the device. Please help.

---

### Post by oldfred on 2010-02-27
I have had my 610 for a year or so with several versions of Ubuntu and I plug it in and it works both on my desktop and on my portable.
Before and after lists from lusub:

fred@fred-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
fred@fred-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=DarkRed]Bus 003 Device 002: ID 066f:82e0 SigmaTel, Inc. [/COLOR]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by KarthikPH on 2010-03-01
Thanks for that. Could you please let me know if you had installed any specific drivers to get ubuntu to recognize the music player?

---

### Post by oldfred on 2010-03-01
I do not think I installed anything. I do install a lot of the normal 'extra' stuff to play mp3's, video's, etc. but I do not think anything I install is for the USB ports.

If you run lsusb before & after to you see the device? If not we need to look for USB errors as you plug in.

---

### Post by KarthikPH on 2010-03-07
Hi, it worked!!! I think the problem was with the USB port. Plugged in the player into another port and it worked smoothly. Ubuntu Rocks!!!

---

### Post by gunjanjamindar on 2012-10-14
Hello,

Same problem here, even after changing USB it did not recognize.
Actually , my transcend was in MTP mode ( media transfer protocol)
I switched to USB mode, then it was automatically mounted on Ubuntu.

For doing this you need to go to Settings in Transcend mp3 and search for MTP/USB modes. 

Regards,

---

### Post by nothingspecial on 2012-10-14
Old thread.

Closed.

---

