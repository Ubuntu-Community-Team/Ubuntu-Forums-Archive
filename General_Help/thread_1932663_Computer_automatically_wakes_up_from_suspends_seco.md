---
title: "Computer automatically wakes up from suspends seconds after entering suspend."
date: 2012-02-27
forum: General Help
---

### Post by Roasted on 2012-02-27
I upgraded some parts recently so my system is now as such:

Intel i3 2100
ASRock H61 Motherboard
250gb Windows 7 SATA HDD
60gb Ubuntu HDD
2x1TB (software raid mirror) Ubuntu Home HDDs
Nvidia GT 440 Graphics Card

I noticed when I came home after putting my computer in suspend mode, it was on. I choked it up to the cat likely hitting a key on the keyboard walking by and tripping the computer to wake up. When I put it in suspend mode later, I heard it fire up as I was still working at the desk. Sure enough, every time I put it in suspend mode, 5-10 seconds later after it fully calms down, it automatically fires up again.

Eh?

---

### Post by Mark Phelps on 2012-02-28
Had similar problems until I changed the BIOS to no longer wake using USB.

---

### Post by Roasted on 2012-02-28
Good thinking... Let me try that...

EDIT - no dice. When I went into my BIOS I found some options, I believe under ACPI configuration? It looked like everything was disabled, including usb mouse, usb keyboard, and ps2 keyboard wake up. I powered my system back into Ubuntu, put it into suspend and it stayed in suspend. Woke it up, gave it 30 seconds, suspended it again, and this time it automatically woke up seconds later. Hmm... :(

---

### Post by pbrane on 2012-02-28
You should go through your BIOS and make sure there are no other "wake on" options. Like wake on LAN.

---

### Post by Roasted on 2012-02-28
> **pbrane said:**
> You should go through your BIOS and make sure there are no other "wake on" options. Like wake on LAN.

Wake on LAN is disabled... :(

---

### Post by Roasted on 2012-02-29
For what it's worth, I'm running an i3 proc, ASRock H61 motherboard, Corsair SSD, 8gb of RAM. Not sure what might be causing this. Is anybody else having this issue? I'm on Ubuntu 11.10 64 bit...

---

### Post by WILD9 on 2012-02-29
I Have exactly the same issue with an Asrock H61 ITX Board. I'm pretty new to linux, pm-suspend.log seems to just show a wakeup event rather than what caused it, is there anywhere that the device initiating the wakeup is logged?

---

### Post by WILD9 on 2012-03-25
Eventually tracked this down to the USB3 Controller, I cant supply a fix unfortunately as I don't need USB3 on my media PC so I disabled the controller in the bios and everything started working properly.

---

### Post by Roasted on 2012-03-25
> **WILD9 said:**
> Eventually tracked this down to the USB3 Controller, I cant supply a fix unfortunately as I don't need USB3 on my media PC so I disabled the controller in the bios and everything started working properly.

I haven't checked on this issue recently to see if there was a BIOS update. I'll have to look into it. Thanks for the insight!

---

