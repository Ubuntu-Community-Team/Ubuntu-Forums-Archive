---
title: "How to communicate with USB0-device after autostart?"
date: 2011-09-22
forum: General Help
---

### Post by inger on 2011-09-22
Hi,
 
I made a program that communicates with two devices, one by ttyUSB0 and one by serial port (ttyS0). I use Lubuntu 11.4.
Now I want to let my program autostart while the PC starts. This works. :wink:
 
But, I am able to communicate with the serial port, **but not the USB0-device**.:sad: 
 
When I start the program by double-click after startup, I can communicate with both devices. This is the same program.
 
Does anybody know what to do to give the startup-user permissions to the USB0-device? I think this is the problem

---

### Post by inger on 2011-09-23
[SOLVED]
This was a timing problem. Now I wait for 15 seconds before the application program open, and then it works very well :grin:

---

