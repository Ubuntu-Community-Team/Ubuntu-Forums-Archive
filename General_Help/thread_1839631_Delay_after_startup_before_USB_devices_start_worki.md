---
title: "Delay after startup before USB devices start working"
date: 2011-09-06
forum: General Help
---

### Post by aldld on 2011-09-06
Hi, I'm currently posting this from a Kubuntu live USB. I'm having this issue on Kubuntu, as well as Xubuntu, and even Linux Mint (I believe an Ubuntu-based version). I did not have this problem with OpenSUSE, however, so I'm assuming it's an Ubuntu-specific issue.

Just a note, I marked this as [all variants] because it affects more than just Kubuntu. I had regular Ubuntu working fairly recently and it didn't have this issue, however that was upgraded from a previous version, so that could be why. I suspect that the same thing would happen with Ubuntu.

When I boot up my computer, my USB keyboard works fine for configuring the BIOS. However once Kubuntu begins booting my keyboard stops working. This lasts for several minutes, until my keyboard suddenly starts working again. (I use a PS/2 mouse, so I can still use that)

The same thing happens with a USB flash drive as well, so it seems to be a problem with USB devices in general.

Here are some lines from /var/log/syslog that look like they might be relevant:

```

Sep  6 04:44:13 ubuntu kernel: [   66.030031] usb 2-3: device descriptor read/64, error -110
Sep  6 04:44:14 ubuntu kernel: [   66.260028] usb 2-3: new high speed USB device using ehci_hcd and address 4
Sep  6 04:44:19 ubuntu kernel: [   71.290111] usb 2-3: device descriptor read/8, error -110
Sep  6 04:44:24 ubuntu kernel: [   76.420118] usb 2-3: device descriptor read/8, error -110
Sep  6 04:44:24 ubuntu kernel: [   76.650025] usb 2-3: new high speed USB device using ehci_hcd and address 5
Sep  6 04:44:29 ubuntu kernel: [   81.680089] usb 2-3: device descriptor read/8, error -110
Sep  6 04:44:34 ubuntu kernel: [   86.810081] usb 2-3: device descriptor read/8, error -110
Sep  6 04:44:34 ubuntu kernel: [   86.920039] hub 2-0:1.0: unable to enumerate USB device on port 3
Sep  6 04:44:35 ubuntu kernel: [   87.330028] usb 5-3: new full speed USB device using ohci_hcd and address 2
Sep  6 04:45:05 ubuntu kernel: [  117.740061] usb 5-3: device descriptor read/64, error -110
Sep  6 04:45:05 ubuntu kernel: [  118.020068] usb 5-3: new full speed USB device using ohci_hcd and address 3
Sep  6 04:45:21 ubuntu kernel: [  133.170077] usb 5-3: device descriptor read/64, error -110
Sep  6 04:45:36 ubuntu kernel: [  148.430056] usb 5-3: device descriptor read/64, error -110
Sep  6 04:45:36 ubuntu kernel: [  148.690060] usb 5-3: new full speed USB device using ohci_hcd and address 4
Sep  6 04:45:41 ubuntu kernel: [  153.720319] usb 5-3: device descriptor read/8, error -110
Sep  6 04:45:46 ubuntu kernel: [  158.850510] usb 5-3: device descriptor read/8, error -110
Sep  6 04:45:46 ubuntu kernel: [  159.110055] usb 5-3: new full speed USB device using ohci_hcd and address 5
Sep  6 04:45:57 ubuntu kernel: [  169.270870] usb 5-3: device descriptor read/8, error -110
Sep  6 04:45:57 ubuntu kernel: [  169.380083] hub 5-0:1.0: unable to enumerate USB device on port 3
Sep  6 04:45:57 ubuntu kernel: [  169.710055] usb 6-1: new low speed USB device using ohci_hcd and address 2
Sep  6 04:45:57 ubuntu kernel: [  170.000245] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.0/input/input4
Sep  6 04:45:57 ubuntu kernel: [  170.000451] generic-usb 0003:06A3:8020.0001: input,hidraw0: USB HID v1.11 Keyboard [Chicony Saitek Eclipse Keyboard] on usb-0000:00:13.1-1/input0
Sep  6 04:45:57 ubuntu kernel: [  170.026137] input: Chicony Saitek Eclipse Keyboard as /devices/pci0000:00/0000:00:13.1/usb6/6-1/6-1:1.1/input/input5
Sep  6 04:45:57 ubuntu kernel: [  170.026434] generic-usb 0003:06A3:8020.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Chicony Saitek Eclipse Keyboard] on usb-0000:00:13.1-1/input1
Sep  6 04:45:57 ubuntu kernel: [  170.026481] usbcore: registered new interface driver usbhid
Sep  6 04:45:57 ubuntu kernel: [  170.026486] usbhid: USB HID core driver
Sep  6 04:45:58 ubuntu kernel: [  170.220048] usb 1-5: new high speed USB device using ehci_hcd and address 4
Sep  6 04:45:58 ubuntu kernel: [  170.373347] scsi12 : usb-storage 1-5:1.0
Sep  6 04:45:59 ubuntu kernel: [  171.370931] scsi 12:0:0:0: Direct-Access     Kingston DataTraveler G2  1.00 PQ: 0 ANSI: 2

```

Thanks, I hope somebody can point me in the right direction (or maybe someone just has better Google-fu than I do :P)

---

### Post by threepot on 2012-02-28
I have this problem too and cannot find a solution, any help would be great.

---

### Post by Mark Phelps on 2012-02-28
Look at your BIOS setting regarding USB legacy devices.  If it is ON, try turning it OFF -- and vice-versa.

---

### Post by threepot on 2012-02-29
After messing and messing I just got a PS2 keyboard and mouse out of storage!

Not really a fix but still a solution :lolflag:

---

### Post by imachavel on 2012-02-29
Motherboards seem to have a thing with hating to boot to a USB device. And sometimes don't like booting when a USB device is in the computer. But keyboard and mouse? I've heard of keyboard and mouse not working if connected after bios loads. Strange, seems your pc doesn't like booting with too many USB devices, especially when you already are booting to a flash drive. I could tell you to check your bios settings, but I doubt this will change anything. Strangely enough, you can read and copy and paste the error message. Perhaps Ubuntu needs an update, or possibly  bios update. Just not sure

---

