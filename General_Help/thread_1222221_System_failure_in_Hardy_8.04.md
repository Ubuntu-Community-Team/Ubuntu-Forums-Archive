---
title: "System failure in Hardy 8.04"
date: 2009-07-24
forum: General Help
---

### Post by mainak_sen on 2009-07-24
I have been using Hardy 8.04 for last 15 months without any problem on my desktop. For the last week or so I have started having 2 major problems.

1. At times the system simply shuts down, without any warning, and for no apparent reasons. This is happening sometimes even when there are no application running. Mine is a 5 year old machine and my initial thoughts were that I am having some hardware problems (CPU overheating, SMPS problems etc.). But tonight I noticed the following log entries (in syslog) just before the time of the shutdown event, and it made me suspicious. Please see the relevant entries in the attached file.

2. This problem started a few days before the 1st one above. Many times, when I boot or reboot, GNOME does not load. Ubuntu seems to load OK (I have the messages turned on in the Ubuntu boot-up splash screen and everything shows OK) but then the logon screen fails to appear. The screen shows a row of color lines near the top, and then goes blank...and stays that way. I have to restart. I dual boot XP and Ubuntu (95% Ubuntu, 5% XP). I have to boot into XP first and then restart afresh before the problem would go away and I would be able to logon to Ubuntu again. 

I am not sure if the above two problems are related in anyway...but since they both started within the last couple of weeks I thought of posting both the issues together.

---

### Post by Rocket2DMn on 2009-07-24
Sounds like your USB hub is acting up - do you have an external one, or is it all internal?  If it's all internal, it could be a hardware problem - perhaps it is not getting a enough power, or whatever is plugging into the USB is trying to draw more power than is available.
Are you able to test the system with a different power supply?
Have you had a kernel upgrade recently?

I'm not sure about your Gnome problem, it may or may not be related.  Difficult to tell without more information.

---

### Post by mainak_sen on 2009-07-24
Thanks Rocket2DMn so much for your response. 

I am attaching the output of sysinfo and lshw, so that you have some more info about my system. Please let me know if there is any other info that might help you and I shall try to provide.

Also, I do not have a spare SMPS lying around...so was not able to check my SMPS.

Thanks again!

---

### Post by philcamlin on 2009-07-24
Jul 25 01:21:42 mainak-desktop kernel: [  188.383007] usb 3-1: device descriptor read/64, error -71
Jul 25 01:21:42 mainak-desktop kernel: [  188.606660] usb 3-1: device descriptor read/64, error -71
Jul 25 01:21:43 mainak-desktop kernel: [  188.822350] usb 3-1: new low speed USB device using uhci_hcd and address 9
Jul 25 01:21:43 mainak-desktop kernel: [  189.353517] usb 3-1: device not accepting address 9, error -71
Jul 25 01:21:43 mainak-desktop kernel: [  189.465363] usb 3-1: new low speed USB device using uhci_hcd and address 10
Jul 25 01:21:44 mainak-desktop kernel: [  189.872732] usb 3-1: device not accepting address 10, error -71
Jul 25 01:21:44 mainak-desktop kernel: [  189.984550] usb 3-1: new low speed USB device using uhci_hcd and address 11
Jul 25 01:21:44 mainak-desktop kernel: [  190.026096] usb 3-1: device descriptor read/all, error -71

it does look like your usb hub is hurting your pc :(

is it possible to unplug it ??and try without them

---

### Post by Rocket2DMn on 2009-07-24
If you can find the dmesg log from that boot, that would be great.  Check in /var/log - there is a dmesg file, and a few archives for it - check the timestamp.

In the meantime I would disconnect all unnecessary hardware from the machine.

It is still quite possible that the USB messages we are seeing aren't really a problem, and that your machine may be overheating or you're suffering from a faulty power supply.  I've had this happen before and it is near impossible to troubleshoot without replacing hardware.

---

