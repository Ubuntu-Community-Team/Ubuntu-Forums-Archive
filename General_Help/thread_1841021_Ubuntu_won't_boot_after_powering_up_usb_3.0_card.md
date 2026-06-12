---
title: "Ubuntu won't boot after powering up usb 3.0 card"
date: 2011-09-08
forum: General Help
---

### Post by geoff13 on 2011-09-08
Hey guys,
 
I recently installed a Gigaware USB 3.0 pci card without molex power. Ubuntu device manager recognizes the card but no devices. 
 
The hub has a 4-pin molex plug. Diverted power from my hard drive to the card using 4-pin splitter. After this the console boots into recovery.
 
Thinking its power issues but could it be something else? there is a 6-pin unused molex that is directly from the power supply but i have been able to find 6 to 4 pin yet.
 
old power supply from a dell dimension 9150
 
would an unrecognized pci card cause a console to not boot?? I wouldn't think so... it would just show up as in a problem state right???
 
any input appreciated

---

### Post by dcstar on 2011-09-09
> **geoff13 said:**
> Hey guys,
 
I recently installed a Gigaware USB 3.0 pci card without molex power. Ubuntu device manager recognizes the card but no devices. 
 
The hub has a 4-pin molex plug. Diverted power from my hard drive to the card using 4-pin splitter. After this the console boots into recovery.
 
Thinking its power issues but could it be something else? there is a 6-pin unused molex that is directly from the power supply but i have been able to find 6 to 4 pin yet.
 
old power supply from a dell dimension 9150
 
would an unrecognized pci card cause a console to not boot?? I wouldn't think so... it would just show up as in a problem state right???
 
any input appreciated

USB 3 cards **require** the external power connection to provide power to the USB devices - USB 3 devices can draw a lot more power than USB 2 or 1 devices and the motherboard bus that the card plugs into is not designed to supply that sort of power.

If the system won't boot with the card plugged in with the power connected then it may not be compatible with your hardware or with Ubuntu/Linux.

---

### Post by egalvan on 2011-09-09
Remove the card, fire up the computer to see if it boots.

If it does, then you have issues with the card.

If it does not, the problem is elsewhere.

---

