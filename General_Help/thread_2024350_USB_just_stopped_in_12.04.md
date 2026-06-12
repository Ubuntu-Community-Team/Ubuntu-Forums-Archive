---
title: "USB just stopped in 12.04"
date: 2012-07-13
forum: General Help
---

### Post by cptncatholic on 2012-07-13
For this past week, I've been using a bluetooth adapter and wireless mouse with Ubuntu Studio 12.04 on my HP Pavilion G6. Today, I was in the middle of work when the system locked up and I couldn't click on anything with the mouse, and I couldn't switch windows or anything.

I pressed the power button to shut the system down and reboot. When I rebooted I had no communication with anything USB. The wireless mouse didn't work, the bluetooth adapter didn't work, no usb drives would mount.

I tried to add "GRUB_CMDLINE_LINUX=”acpi=force irqpoll”" to /etc/grub/default, but that didn't fix it.

I also tried to 'sudo apt-get purge irqbalance' but that didn't work either.

I don't know if this is a result of a recent update either, but I need to get this USB working again. I keep most of my datafiles on USB drives and need to get to them.

Thanks!

---

### Post by Rexilion on 2012-07-14
Did you try using your USB hardware on another PC? Maybe it just died??

---

### Post by cptncatholic on 2012-07-14
Yes. The USB devices still worked on another computer. I even booted from the install CD and the USB ports worked then. When I booted back into the system, the USB ports started working again. I don't know if/how booting from the install CD fixed the problem, but they are working again and I can get my stuff done! :)

---

