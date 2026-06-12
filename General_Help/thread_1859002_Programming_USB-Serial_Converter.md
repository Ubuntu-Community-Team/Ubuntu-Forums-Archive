---
title: "Programming USB-Serial Converter"
date: 2011-10-13
forum: General Help
---

### Post by Rezzz on 2011-10-13
Hi,

I bought an USB-serial converter (Plugable USB to RS-232 DB9 Serial Adapter) recently. It uses the LS2303 chipset. I am trying to send some command to a serial controlled device and hopefully I could write a program so that it can run automatically.

I have struggled with it for a couple of days, but don't have much idea. Is there any suggestions how should I approach the problem?

Thanks in advance,

---

### Post by dcstar on 2011-10-15
> **Rezzz said:**
> Hi,

I bought an USB-serial converter (Plugable USB to RS-232 DB9 Serial Adapter) recently. It uses the LS2303 chipset. I am trying to send some command to a serial controlled device and hopefully I could write a program so that it can run automatically.

I have struggled with it for a couple of days, but don't have much idea. Is there any suggestions how should I approach the problem?

Thanks in advance,

```
man ttys
ls /dev/tty*
```

---

