---
title: "Mouse takes minutes to start working after boot"
date: 2010-10-13
forum: General Help
---

### Post by kamina on 2010-10-13
This is kind of cross post from the 10.10 beta forum, but since [that thread](http://ubuntuforums.org/showthread.php?t=1579693) went by without a solution, forum (and thread) are locked and this problem still exists, I'll try again. :)

When I reboot my machine, it seems to go pretty quickly. However looking at the log it seems that most everything is running after about 8.6 seconds, and then USB starts loading up. The first log entry regarding USB comes at 32 seconds, second one at 62 seconds. The keyboard starts working at 84 seconds and the mouse at 166 seconds.

Note, this same system was running 9.10, 10.4 and various other distros I tested without such problems...

I've removed all hubs, everything is directly connected to the computer.

boot.log
```

Oct 13 08:19:16 mikaa-desktop kernel: [    8.662947] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Oct 13 08:19:40 mikaa-desktop kernel: [   32.201676] usb 2-3: new high speed USB device using ehci_hcd and address 3
Oct 13 08:20:10 mikaa-desktop kernel: [   62.686157] usb 2-3: new high speed USB device using ehci_hcd and address 4
Oct 13 08:20:15 mikaa-desktop kernel: [   67.050888] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Oct 13 08:20:21 mikaa-desktop kernel: [   73.185664] usb 2-3: new high speed USB device using ehci_hcd and address 5
Oct 13 08:20:31 mikaa-desktop kernel: [   83.836865] usb 3-1: new low speed USB device using uhci_hcd and address 2
Oct 13 08:20:32 mikaa-desktop kernel: [   84.037743] usbcore: registered new interface driver hiddev
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052424] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052524] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052549] usbcore: registered new interface driver usbhid
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052551] usbhid: USB HID core driver
Oct 13 08:20:32 mikaa-desktop kernel: [   84.311994] usb 7-1: new full speed USB device using uhci_hcd and address 2
Oct 13 08:21:02 mikaa-desktop kernel: [  114.796415] usb 7-1: new full speed USB device using uhci_hcd and address 3
Oct 13 08:21:33 mikaa-desktop kernel: [  145.280891] usb 7-1: new full speed USB device using uhci_hcd and address 4
Oct 13 08:21:43 mikaa-desktop kernel: [  155.780372] usb 7-1: new full speed USB device using uhci_hcd and address 5
Oct 13 08:21:54 mikaa-desktop kernel: [  166.240098] usb 1-5.3: new low speed USB device using ehci_hcd and address 4
Oct 13 08:21:54 mikaa-desktop kernel: [  166.341005] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3:1.0/input/input3
Oct 13 08:21:54 mikaa-desktop kernel: [  166.341184] generic-usb 0003:046D:C043.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.7-5.3/input0
```

edit:

kernel.log
```

Oct 13 08:19:16 mikaa-desktop kernel: [    8.201231] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445457126538249295 new 18445457126555515922 attempts 1
Oct 13 08:19:16 mikaa-desktop kernel: [    8.662947] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Oct 13 08:19:23 mikaa-desktop kernel: [   15.957408] eth0: no IPv6 routers present
Oct 13 08:19:24 mikaa-desktop kernel: [   16.799745] usb 2-3: device descriptor read/64, error -110
Oct 13 08:19:24 mikaa-desktop kernel: [   16.851624] vmnet1: no IPv6 routers present
Oct 13 08:19:24 mikaa-desktop kernel: [   16.867596] vmnet8: no IPv6 routers present
Oct 13 08:19:39 mikaa-desktop kernel: [   31.986098] usb 2-3: device descriptor read/64, error -110
Oct 13 08:19:40 mikaa-desktop kernel: [   32.201676] usb 2-3: new high speed USB device using ehci_hcd and address 3
Oct 13 08:19:55 mikaa-desktop kernel: [   47.284227] usb 2-3: device descriptor read/64, error -110
Oct 13 08:20:10 mikaa-desktop kernel: [   62.470574] usb 2-3: device descriptor read/64, error -110
Oct 13 08:20:10 mikaa-desktop kernel: [   62.686157] usb 2-3: new high speed USB device using ehci_hcd and address 4
Oct 13 08:20:15 mikaa-desktop kernel: [   67.050888] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
Oct 13 08:20:21 mikaa-desktop kernel: [   73.073929] usb 2-3: device not accepting address 4, error -110
Oct 13 08:20:21 mikaa-desktop kernel: [   73.185664] usb 2-3: new high speed USB device using ehci_hcd and address 5
Oct 13 08:20:31 mikaa-desktop kernel: [   83.573367] usb 2-3: device not accepting address 5, error -110
Oct 13 08:20:31 mikaa-desktop kernel: [   83.573383] hub 2-0:1.0: unable to enumerate USB device on port 3
Oct 13 08:20:31 mikaa-desktop kernel: [   83.836865] usb 3-1: new low speed USB device using uhci_hcd and address 2
Oct 13 08:20:32 mikaa-desktop kernel: [   84.037743] usbcore: registered new interface driver hiddev
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052424] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052524] generic-usb 0003:046D:C312.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.0-1/input0
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052549] usbcore: registered new interface driver usbhid
Oct 13 08:20:32 mikaa-desktop kernel: [   84.052551] usbhid: USB HID core driver
Oct 13 08:20:32 mikaa-desktop kernel: [   84.311994] usb 7-1: new full speed USB device using uhci_hcd and address 2
Oct 13 08:20:47 mikaa-desktop kernel: [   99.394481] usb 7-1: device descriptor read/64, error -110
Oct 13 08:21:02 mikaa-desktop kernel: [  114.580834] usb 7-1: device descriptor read/64, error -110
Oct 13 08:21:02 mikaa-desktop kernel: [  114.796415] usb 7-1: new full speed USB device using uhci_hcd and address 3
Oct 13 08:21:17 mikaa-desktop kernel: [  129.878946] usb 7-1: device descriptor read/64, error -110
Oct 13 08:21:33 mikaa-desktop kernel: [  145.065812] usb 7-1: device descriptor read/64, error -110
Oct 13 08:21:33 mikaa-desktop kernel: [  145.280891] usb 7-1: new full speed USB device using uhci_hcd and address 4
Oct 13 08:21:43 mikaa-desktop kernel: [  155.668586] usb 7-1: device not accepting address 4, error -110
Oct 13 08:21:43 mikaa-desktop kernel: [  155.780372] usb 7-1: new full speed USB device using uhci_hcd and address 5
Oct 13 08:21:54 mikaa-desktop kernel: [  166.168105] usb 7-1: device not accepting address 5, error -110
Oct 13 08:21:54 mikaa-desktop kernel: [  166.168120] hub 7-0:1.0: unable to enumerate USB device on port 1
Oct 13 08:21:54 mikaa-desktop kernel: [  166.240098] usb 1-5.3: new low speed USB device using ehci_hcd and address 4
Oct 13 08:21:54 mikaa-desktop kernel: [  166.341005] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.3/1-5.3:1.0/input/input3
Oct 13 08:21:54 mikaa-desktop kernel: [  166.341184] generic-usb 0003:046D:C043.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.7-5.3/input0
```

---

### Post by kamina on 2010-10-13
Seems the problem is the integrated memory card reader, don't know why it worked with all other releases. After unplugging it everything works fine again.

---

### Post by ghostborg on 2011-01-09
Thanks so much !!!! This problem was very annoying. I too had an internal memory card reader that I installed about two years ago (Rosewill) that worked fine until Ubuntu 10.10. I unplugged it and viola everything started working normally.

---

