---
title: "USB Dongle for CAT5 KVM not recognized"
date: 2010-09-09
forum: General Help
---

### Post by krimzen85 on 2010-09-09
Hi All,
 
I have a two node, source/destination laboratory that I've built for testing at my place of employment. I have 4 servers on each side for different protocol testing: two Windows and two Linux all daisy-chained through a CAT5 KVM switch. I obviously have network switches in place as well, but that's irrelevant for this issue:
 
I am connecting the servers to the CAT5 KVM with CAT5 to DB-9 & USB Dongles. The DB-9 is the VGA and the USB is for mouse/keyboard support through the KVM. What I've found is that all of the Windows recognize the USB connection for keyboard/mouse (this connection also must be in place for the KVM to discover the server), and 1 Linux Server recognizes the USB connection. **The other 3 Linux servers do not recognize the USB keyboard/mouse support portion of the dongle, and subsequently the KVM cannot discover them.**
 
The server hardware should be identical on all servers, and I've set the BIOS/CMOS in all servers to mirror each other. Additionally, if I plug the USB portion of the dongle into one of the Windows [COLOR=#003d7d][IMG]http://konac.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG][/COLOR]and the VGA into the problematic Linux server, the KVM recognizes it (I can see it, but I obviously can't type or use the mouse). So I am confident beyond a reasonable doubt that this is an issue with USB Keyboard/Mouse support somewhere in my install of Ubuntu 9.04 Jaunty Jackalope on 3/4 of these.
 
It must be possible, however, because 1 of them works. I've checked portions of the working Linux Server to compare them against each other, and I can't find anything that really stands out or explains why it works and the rest don't. Hell, the working one doesn't even have any drivers installed on it.
 
The easy fix is to purchase a PS/2 Dongle. I've already verified it can support it via PS/2, but I don't want to just band-aid the issue unless there is no other solution.
 
Any help is most appreciated.

---

