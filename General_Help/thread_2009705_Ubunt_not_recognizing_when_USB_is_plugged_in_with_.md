---
title: "Ubunt not recognizing when USB is plugged in with Samsung SPH-M930  phone"
date: 2012-06-24
forum: General Help
---

### Post by xaegis on 2012-06-24
I am Running Ubuntu 12.04  x64. When I plug the USB cable in from my Samsung SPH-M930 phone, it doesn't seem to want to mount the device. It recognizes it in lsusb, but will not mount.

```

Me@MyComputer:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0c45:640f Microdia 
***Bus 002 Device 009: ID 04e8:f000 Samsung Electronics Co., Ltd ***
Bus 002 Device 004: ID 046d:c06b Logitech, Inc. G700 Wireless Gaming Mouse
Bus 002 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 006: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 007: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 002 Device 008: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card



```

Anyone have any ideas on how to begin troubleshooting this problem?

thanks in advance,

-e

---

### Post by jack454 on 2012-06-24
I had to create a file called 51-android.rules in /etc/udev/rules.d. You can try creating that file and putting this in it. SUBSYSTEMS=="usb", ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="f000", MODE="0666"

---

### Post by xaegis on 2012-06-24
> **jack454 said:**
> I had to create a file called 51-android.rules in /etc/udev/rules.d. You can try creating that file and putting this in it. SUBSYSTEMS=="usb", ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="f000", MODE="0666"

Thanks... What does it to? Change the owner of the USB module to R/W everyone? :)

I was beginning to think it is some kind of permissions issue because Turning the USB onto debugging mode fixes the problem as well.

---

### Post by jack454 on 2012-06-24
It should make the computer recognize your phone. You may have to restart the computer after creating the file. Hope it works for you, that's what I had to do to get my phone to show up.

---

### Post by xaegis on 2012-06-24
> **jack454 said:**
> It should make the computer recognize your phone. You may have to restart the computer after creating the file. Hope it works for you, that's what I had to do to get my phone to show up.

I just tried it and restarted my computer. It (creating the file and inserting it into the /etc/udev/rules.d directory) didnt do anyting for me. THe /etc/udev/ on the computer and not the phone. Correct?

---

### Post by jack454 on 2012-06-24
Right. on the computer. Sorry it didn't work. not sure what to try now.

---

### Post by DisturbedDragon on 2012-06-24
When you plug the phone in be sure to select USB Storage option.  Requires two screen taps when prompted on the phone.  Make sure it is not going to Charge Only option by default in you phone settings.  Ensure the USB cable you are using is a host cable and not just a charging cable.

---

### Post by xaegis on 2012-06-24
> **DisturbedDragon said:**
> When you plug the phone in be sure to select USB Storage option.  Requires two screen taps when prompted on the phone.  Make sure it is not going to Charge Only option by default in you phone settings.  Ensure the USB cable you are using is a host cable and not just a charging cable.

Host cable? Hummm... I tried several different cables and none of them worked including cables which worked for data transfer with my LG phone. I never knew there were differentiated cables.

I was placing it in Mass Storage mode and not charge only mode.

Thanks everyone for trying to help me!

:)

---

### Post by DisturbedDragon on 2012-06-24
abraham@Abraham-N150:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
[COLOR=Blue]Bus 001 Device 003: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone

[COLOR=Black]My usb output 12.04 x86.  I notice the phone is further identified.  Perhaps the phone is not properly communicating its ID.  Have you tried other USB ports or computers? About all I have for you.  Sorry if it does not help.[/COLOR]
[/COLOR]

---

### Post by xaegis on 2012-06-24
> **DisturbedDragon said:**
> abraham@Abraham-N150:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
[COLOR=Blue]Bus 001 Device 003: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone

[COLOR=Black]My usb output 12.04 x86.  I notice the phone is further identified.  Perhaps the phone is not properly communicating its ID.  Have you tried other USB ports or computers? About all I have for you.  Sorry if it does not help.[/COLOR]
[/COLOR]

Yes I have tried it with 1 other computer with the same outcome.

Thanks though.

---

### Post by ramjr on 2012-11-28
I've just gotten this phone as well and am having the same issues.  I can add details about the failure, but no solution :(

It is not recognized by 3 different Linux/x86-64 systems, one Kubuntu (10.10, I believe), one Linux Mint, both AMD based desktop systems; and Ubuntu Studio running on an AMD based laptop.

It also fails on a Macbook Pro running Lion.

However, a Dell laptop with Windows 7 sees it as a drive without any problems.

---

### Post by xaegis on 2012-11-28
> **ramjr said:**
> I've just gotten this phone as well and am having the same issues.  I can add details about the failure, but no solution :(

It is not recognized by 3 different Linux/x86-64 systems, one Kubuntu (10.10, I believe), one Linux Mint, both AMD based desktop systems; and Ubuntu Studio running on an AMD based laptop.

It also fails on a Macbook Pro running Lion.

However, a Dell laptop with Windows 7 sees it as a drive without any problems.A workaround that I found which works is to enable USB Debugging mode. it is under the Applications menu in the settings folder.
It is a little annoying but it functions more or less. But I think it is a security risk.
HTH,
Axe.

---

### Post by ramjr on 2012-11-29
Yes, thanks, I'd seen that suggestion made by someone else.  Thanks.

I also have the following, from /var/log/syslog, which may help someone figure this out:

Nov 15 22:06:11 kernel: [   76.127084] usb 1-2: new high-speed USB device number 4 using ehci_hcd
Nov 15 22:06:11 mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:0b.1/usb1/1-2"
Nov 15 22:06:11 mtp-probe: bus: 1, device: 4 was not an MTP device
Nov 15 22:06:12 kernel: [   76.337116] Initializing USB Mass Storage driver...
Nov 15 22:06:12 kernel: [   76.337305] scsi6 : usb-storage 1-2:1.0
Nov 15 22:06:12 kernel: [   76.337422] usbcore: registered new interface driver usb-storage
Nov 15 22:06:12 kernel: [   76.337425] USB Mass Storage support registered.
Nov 15 22:06:12 kernel: [   76.444806] usbcore: registered new interface driver uas
Nov 15 22:06:13 kernel: [   77.342427] scsi 6:0:0:0: Direct-Access     Qualcomm  IncorporatedMas s st PQ: 0 ANSI: 2
Nov 15 22:06:13 kernel: [   77.343623] sd 6:0:0:0: Attached scsi generic sg3 type 0
Nov 15 22:06:13 kernel: [   77.347514] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Nov 15 22:06:13 usb_modeswitch: switching device 04e8:f000 on 001/004
^?$ 

The above would indicate partial recognition of the phone, but no device node is created:

$ ls /dev/sd?
/dev/sda  /dev/sdb

---

