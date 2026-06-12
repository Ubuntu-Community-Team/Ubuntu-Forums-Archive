---
title: "Why no hibernate with inactivity?"
date: 2012-01-26
forum: General Help
---

### Post by ferulebezel on 2012-01-26
When I got to the Power section of System Settings there is only the option to suspend after a period of inactivity.  I have lots of peripherals and semi-peripherals plugged into a usb controlled power strip.  The problem is that suspending leave usb power on while hibernate doesn't.  

How do I get it to hibernate after a fixed period of inactivity?

---

### Post by Frogs Hair on 2012-01-26
If it is a Wubi installation hibernation is not possible . If you set up a swap partition when you installed I don't know why there would be no hibernate option .

---

### Post by C.S.Cameron on 2012-01-27
Yes you need a swap partition for Ubuntu to dump the active memory into.
It should be larger that your RAM size.

---

### Post by ferulebezel on 2012-01-27
It lets me hibernate from the menu when I use the "ubuntu" GUI (for some reason it isn't on the gnome one) but there isn't an option to hibernate instead of suspend in in the power section of the system settings so it isn't a swap partition problem.  

I didn't use Wubi,  I installed from a disk several versions and have done several dist upgrades since.

---

