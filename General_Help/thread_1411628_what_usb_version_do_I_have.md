---
title: "what usb version do I have?"
date: 2010-02-20
forum: General Help
---

### Post by garyed on 2010-02-20
Is there a terminal command that will tell me what version usb I have?

---

### Post by howefield on 2010-02-20
Try

```
lsusb
```

---

### Post by garyed on 2010-02-20
> **howefield said:**
> Try

```
lsusb
```
I'm not sure that tells me what version I have.
Here are my results:
> [QUOTE]Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 [/QUOTE]

---

### Post by howefield on 2010-02-20
Hmm, sorry about that, it gives me (as well as the actual USB devices which I stripped out for clarity).

> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by garyed on 2010-02-23
> **howefield said:**
> Hmm, sorry about that, it gives me (as well as the actual USB devices which I stripped out for clarity).
I think that my output is what you get if you have usb 1.x & your output is what you get if you have 2.x. I tried "lsusb" on a computer I know has usb 2.0 & i got the same output as you did.
Thanks

---

