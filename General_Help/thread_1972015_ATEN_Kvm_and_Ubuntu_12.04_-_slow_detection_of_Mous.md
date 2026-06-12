---
title: "ATEN Kvm and Ubuntu 12.04 - slow detection of Mouse/Keyboard"
date: 2012-05-03
forum: General Help
---

### Post by smurphy on 2012-05-03
I have a strange/weird phenomena on my systems.
Having a Mac Mini 2012/8GB Ram, and a Dell Precision M4600/16GB Ram connected to a philips Brillance 273P screen, and a MK710 Mouse/Keyboard combination using a ATEN KVM CS682

Now - when I first installed ubuntu (Actually, Kubuntu 12.04 - but the underlying mouse/keyboard detection shouldn´t be affected) - everything worked fine (Ok, had to reconfigure the grub on the Dell ;) )...

On the DELL M4600 - everything is smooth out of the Box. This one, work machine, I have upgraded from 8.04 -> 9.04 -> 10.04 -> 11.04 and 12.04 LTS. I am using a graphic Chip, AMD Radeon HD 6700M Series and the corresponding restricted driver.

The Mac Mini, as I had the issues before - I have made a plain/clean install of the OS partition, and  zeroed out the KDE/Desktop configuration. restricted drivers for the NVidia GeForce 320M used here.

The KVM Switch used is a ATEN CS682

Now - when switching from the Mac Mini to the Dell, Mouse/Keyboard is there almost instantly.

Switching from the Dell to the Mac Mini, I have a 15Seconds delay until the Mouse/Keyboard is responsive.

SO:

Dell M4600 -> Mac Mini: Delay 15secs
Mac Mini -> Dell M4600: Delay 0secs


The Thing is - on the M4600 the mouse is detected once, and stays ... (according to a dmesg output).
On the Mac-Mini, mouse detection is done every time I come back into.

And - just for the logs - the first 2 days after the installation of 12.04, switching from the DELL to the Mac Mini was fast/smooth as the other way around. It just started after some days of use - to take time to enable mouse/keyboard (avg. 15secs) from Dell -> Mac mini.

Anyone knows what causes this behavior ? It is kind of annoying TBH...

Here - detection of the Mouse/Keyboard on the Mac mini:
```
[ 7168.474128] usb 1-4: USB disconnect, device number 10
[ 7190.436090] usb 1-4: new high-speed USB device number 11 using ehci_hcd
[ 7190.569325] hub 1-4:1.0: USB hub found
[ 7190.569421] hub 1-4:1.0: 3 ports detected
[ 7190.574620] usb 4-4.1: USB disconnect, device number 15
[ 7190.857716] usb 4-4.1: new full-speed USB device number 16 using ohci_hcd
[ 7191.050779] logitech-djreceiver 0003:046D:C52B.0034: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:06.0-4.1/input2
[ 7191.074154] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:06.0/usb4/4-4/4-4.1/4-4.1:1.2/0003:046D:C52B.0034/input/input25
[ 7191.074366] logitech-djdevice 0003:046D:C52B.0036: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:06.0-4.1:1
[ 7191.082376] input: Logitech Unifying Device. Wireless PID:2008 as /devices/pci0000:00/0000:00:06.0/usb4/4-4/4-4.1/4-4.1:1.2/0003:046D:C52B.0034/input/input26
[ 7191.082507] logitech-djdevice 0003:046D:C52B.0037: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2008] on usb-0000:00:06.0-4.1:2

```

On the Dell M4600 - only the KVM USB Hub is redetected.
```
[ 6523.871302] usb 1-1.2.2: new high-speed USB device number 14 using ehci_hcd
[ 6523.963762] hub 1-1.2.2:1.0: USB hub found
[ 6523.963966] hub 1-1.2.2:1.0: 3 ports detected
[ 6580.313239] usb 1-1.2.2: USB disconnect, device number 14
[ 7106.395621] usb 1-1.2.2: new high-speed USB device number 15 using ehci_hcd
[ 7106.488435] hub 1-1.2.2:1.0: USB hub found
[ 7106.488597] hub 1-1.2.2:1.0: 3 ports detected
[ 7128.059789] usb 1-1.2.2: USB disconnect, device number 15
```

The initial Mouse/Kayboard detection on the Dell M4600 is as follows:
```
[   87.137780] usb 1-1.2.2: USB disconnect, device number 9
[   92.324045] usb 1-1.2.2: new high-speed USB device number 10 using ehci_hcd
[   92.416815] hub 1-1.2.2:1.0: USB hub found
[   92.416854] hub 1-1.2.2:1.0: 3 ports detected
[   95.522184] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.1.3.1/input2
[   95.542400] input: Logitech Unifying Device. Wireless PID:101b as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.1/1-1.1.3.1:1.2/0003:046D:C52B.0003/input/input15
[   95.542635] logitech-djdevice 0003:046D:C52B.0005: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101b] on usb-0000:00:1a.0-1.1.3.1:1
[   95.550457] input: Logitech Unifying Device. Wireless PID:2008 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.3/1-1.1.3.1/1-1.1.3.1:1.2/0003:046D:C52B.0003/input/input16
[   95.550586] logitech-djdevice 0003:046D:C52B.0006: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2008] on usb-0000:00:1a.0-1.1.3.1:2

```

My question is - why is the Mac Mini always redetecting the Keyboard/Mouse ? It didn't do it in the beginning ?
Any hints ? Ideas on how to influence that behavior ?
Thx

---

### Post by smurphy on 2012-05-07
As usual - under linux, I have to find my answer myself, and so did this time around.

To make a long story short - the ATEN KWM switch can do a "Mouse emulation function". If you disable it, it works flawlessly.

The reason it worked on my M4600 without a 15Sec think-time, was that the Virtual-box (I think/suspect it) grabbed the mouse config and wouldn't release it. If I disable Virtualbox, I have the same issue. It seems that the mouse emulation caused UBuntu to first discard the old config, scan the USB Bus again, and reconfigure the mouse/keyboard (evdev) every time when the Switch enabled the mouse emulation. The thing is that Linux detected the real mouse/keyboard and enabled these drivers in turn. So - we always had a race between the driver/device detection running.
Note - that this happened also when switching system, to the system that you just left. The Mouse/Keyboard got reconfigured.

As a side note - if anyone is using this KVM Switch on a mac Mini under Mac OS-X too, enable the DynaSync function. It will enable Mac OS-X to not resync the screen every 15Seconds ...

---

