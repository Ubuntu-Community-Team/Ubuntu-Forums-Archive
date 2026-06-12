---
title: "pantech jest"
date: 2010-11-27
forum: General Help
---

### Post by rob3048 on 2010-11-27
i just recently bought a pantech jest. i want to put the music i have on my computer onto by plugging it in and dragging a dropping the files. i have the latest version of ubuntu. when i plug my phone in, my phone says it's synced but it doesn't show up on the computer anywhere. i tried it on my friends windows computer and it worked fine so im guessing its ubuntu. any suggestions?

---

### Post by dwe1982 on 2011-04-06
I'm having the same issue.  I've even gone so far as to integrate USB drivers into wine and run Pantech's PC Suite through Wine.  Didn't help at all.

---

### Post by Krothie on 2011-07-31
Hey Ive had the pantech jest for a while and I have the same problem as the both of you. but I can tell you that it can find the phone when you sync music. if you type in      lsusb        
```
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 013: ID 106c:320f Curitel Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

And when you unplug your phone you will get this:

```
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So after that test I found out that the Pantech Jest on my PC is

```
Bus 002 Device 013: ID 106c:320f Curitel Communications, Inc. 
```






I have no idea if this helps but Ubuntu does find my phone just how to use it is another question.  
If anyone can continue this it will be very helpful. Thank you!

---

