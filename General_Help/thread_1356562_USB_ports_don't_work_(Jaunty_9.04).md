---
title: "USB ports don't work (Jaunty 9.04)"
date: 2009-12-16
forum: General Help
---

### Post by hathiphnath on 2009-12-16
Hi all!

I upgraded one the PCs in my household to 9.04 a while ago and recently noticed that the USB ports doesn't work. At first I thought the issue was in my memory-stick, but then I recalled that every successful use of USB ports happens when dual-booted to Windows.

So, how could I solve the issue? The specs are in the signature.

P.S.
Upgrading to 9.10 and praying it would solve the issue isn't a good option as the owner of the PC isn't a fan of upgrading the OS. :(

---

### Post by philinux on 2009-12-16
Open a terminal and post back the output of 

```
lsusb
```

---

### Post by hathiphnath on 2009-12-18
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by hathiphnath on 2010-02-16
Is the issue too obscure? :-(

---

