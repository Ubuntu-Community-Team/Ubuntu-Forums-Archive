---
title: "finding out NIC modules"
date: 2006-03-05
forum: General Help
---

### Post by chocolatetoothpaste on 2006-03-05
How do I find out which module a NIC is using?  I have tried various modprobes, but I can't seem to get the right parameters.  My second NIC is a RealTEK 8139+  so it is using the 8139too module,  but my other is a Digital Equipment Corp  DECchip 21140, and I need to find out which module it uses. Thanks in advance.

---

### Post by chocolatetoothpaste on 2006-03-05
More specific to my problem, I am trying to setup a devil linux firewall, and I apparently I have to assing the modules manually, so I need to know how to view which modules my cards are using.  modprobe tells me what modules are running, but not what card is using them.  Does that make sense?

---

### Post by ranf on 2006-03-06
You can install the package `hwinfo' and then run
```
hwinfo --network
```

It also tells you which modules a hardware needs. But if you need specific parameters for a kernel module it won't tell you that.

```
modinfo <module>
```
lists possible parameters though.

---

