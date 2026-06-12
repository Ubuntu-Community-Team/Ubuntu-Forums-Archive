---
title: "USB not detected - Ubuntu 9.04"
date: 2009-08-24
forum: General Help
---

### Post by Chris13243 on 2009-08-24
Hello all, thanks in advance for any insight on this!

I've been searching the forums and google for a solution but nothing I have tried has worked yet.

The problem is that when I plug in a USB stick Ubuntu does not recognise it or even register that it is there. Both usbmount and pmount are installed but I'm not sure how to check whether the drives are actually functioning.

Any advice would help immensely!

Thanks,
Chris

---

### Post by uylug on 2009-08-24
> **Chris13243 said:**
> Hello all, thanks in advance for any insight on this!

I've been searching the forums and google for a solution but nothing I have tried has worked yet.

The problem is that when I plug in a USB stick Ubuntu does not recognise it or even register that it is there. Both usbmount and pmount are installed but I'm not sure how to check whether the drives are actually functioning.

Any advice would help immensely!

Thanks,
Chris

What is the ouput of

```
lsusb
```

---

### Post by Chris13243 on 2009-08-25
Hi there, thanks for the reply...

The output from this command is as follows:

```

Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Thanks
Chris

---

