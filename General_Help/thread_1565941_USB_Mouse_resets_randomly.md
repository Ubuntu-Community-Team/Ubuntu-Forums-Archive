---
title: "USB Mouse resets randomly"
date: 2010-09-01
forum: General Help
---

### Post by sobah123 on 2010-09-01
Hi there,  for the past 3 months ( since I upgraded to 10.04 TLS ), I am getting random USB mouse resets.  The glitch lasts for about 1-2 seconds but is very annoying while I am playing a game. ( it also happens at any given moment, web browsing or just plain idle ).   

Here is what I could find in both kern.log and syslog files. 
Sep  1 17:36:18 homebox kernel: [17561.172517] usb 3-3: reset low speed USB device using ohci_hcd and address 2
Sep  1 17:36:41 homebox kernel: [17584.228519] usb 3-3: reset low speed USB device using ohci_hcd and address 2
Sep  1 17:37:05 homebox kernel: [17608.212534] usb 3-3: reset low speed USB device using ohci_hcd and address 2
Sep  1 17:37:26 homebox kernel: [17629.060520] usb 3-3: reset low speed USB device using ohci_hcd and address 2

( similar entries appear each time this bug surfaces )

I tried for several weeks to find correlating information as to why this would happen, to no avail. Also read countless posts of similar issues but no threads seem to give any resolution or fix. I tried other mice and it still does that. I am pretty confident it's not my motherboard as the problem started the very moment I upgraded to 10.04. Problem happens no matter which port I plug my mouse into.

Any help is appreciated. 
Thanks

---

### Post by garyedwardjohnston on 2010-09-01
try adjusting your usb settings in bios

change from high speed to full speed or 3.0 to 1.0 or something like this

---

### Post by sobah123 on 2010-09-01
Tried that, didnt work unfortunately :(

---

### Post by garyedwardjohnston on 2010-09-02
i think its related to the speed of your mouse vs the usb port

---

