---
title: "Computer not identifying phone via USB"
date: 2011-07-23
forum: General Help
---

### Post by groonrix on 2011-07-23
I'm trying to connect my phone (Sony Ericsson K800i) to my computer (Ubuntu 10.04).
During Wammu's installation wizard, I was asked for the USB port name under /dev.

To find it, I used *lsusb*, and swapped my mouse connection with my phone.
before:
```

$ lsusb
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04d9:0025 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```after:
```
$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 026: ID 04d9:0025 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Although the computer does not seem to recognize the phone,
The phone does recognizes the connection (it starts a series of dialogs).

How can I make the computer recognize the phone?

---

### Post by thegoonden on 2011-09-20
Ubuntu have wrecked this I'm afraid. I have the exact same problem, with the same phone. My brother's gentoo has no issues, nor does w*nd*ws
Way to go Ubuntu, yeeeeaaaah for driving users away, 10/10.

Hours of searching found loads of people with the problem and not one answer......indicating that either ubuntu really IS the Linux for the not so bright, or that it just cannot be made to work.

I think it's cos of the stupid way it relies on high level programs to create devices instead of the kernel.


Rather annoyed as all my holiday snaps are trapped until I can to a properly working linux or even the dark side.

---

