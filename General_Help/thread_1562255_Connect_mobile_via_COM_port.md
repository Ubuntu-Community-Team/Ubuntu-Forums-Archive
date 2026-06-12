---
title: "Connect mobile via COM port"
date: 2010-08-27
forum: General Help
---

### Post by betacheer on 2010-08-27
I have older Siemens mobile phone and I decided to play with it. I wanted to flash firmware, patch it and so. But how can I determin on which port is it connected. Mobile is not turned on, so can I see which port physically exists and a cable is connected to. Any help ?

---

### Post by LowSky on 2010-08-27
the phone has to be turned on
once connected just type

lshw

---

### Post by betacheer on 2010-08-27
Ok. I have done it.

But I will conect through WINE. Which number have thisCOM port?

```
*-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)

```

---

