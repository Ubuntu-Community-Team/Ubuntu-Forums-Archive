---
title: "Wierd webcam problem"
date: 2011-07-23
forum: General Help
---

### Post by GrizzleNizzle on 2011-07-23
My webcam only works in Cheese, Skype, etc. when it's plugged into 1 of the 2 usb ports on the front.  If I move it to the back where I want it (for aesthetics), and change nothing else, it won't work.

What gives?  :?

---

### Post by squaregoldfish on 2011-07-23
Faulty USB port, probably.

Have a look at /var/log/syslog when you're pluggung/unplugging the webcam, and see what messages are displayed.

Steve.

---

### Post by GrizzleNizzle on 2011-07-23
Syslog shows the usb drive working.  It shows this after I plug in the webcam:

 usb 9-4: new high speed USB device using xhci_hcd and address 0

I can read from a USB drive in the same USB port as well.

Confused...

---

### Post by squaregoldfish on 2011-07-23
I assume it says the same thing regardless of which port it's plugged into.

Faults in USB ports can be strange - the devices you plug into them draw different levels of power (webcams are hungry, USB sticks not). If the port is marginal on whether it works or not, the power draw can be the difference.

Steve.

---

### Post by GrizzleNizzle on 2011-07-23
Thanks for the info.  Do you know of any way to test that theory?

---

### Post by squaregoldfish on 2011-07-23
No idea. Sorry.

---

### Post by no2498 on 2011-07-23
a piece of dust will kill them too

---

