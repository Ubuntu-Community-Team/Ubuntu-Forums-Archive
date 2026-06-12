---
title: "ATI mystery VGA controller ..."
date: 2010-01-07
forum: General Help
---

### Post by Bucky Ball on 2010-01-07
Hi all,

What do people make of this? New Compaq 610. Thought I might have a look around for some drivers, although it's working not bad with the open-source, and this is what lspci gives me:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9552
```Unknown device 9552?

---

### Post by dcstar on 2010-01-07
> **Bucky Ball said:**
> Hi all,

What do people make of this? New Compaq 610. Thought I might have a look around for some drivers, although it's working not bad with the open-source, and this is what lspci gives me:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9552
```Unknown device 9552?
8.04 will not have data about hardware released since then.
```
sudo update-pciids
sudo update-usbids
```
I actually run this in a monthly cron job just to keep up with things.

---

### Post by Bucky Ball on 2010-01-07
```
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
```

Worked a treat. Thanks David. Will now try and find an appropriate driver. Cheers. ;)

---

### Post by Bucky Ball on 2010-01-07
Tried envyng and finds no driver for ATI 4300 anyhow. Open source drivers it is until ATI start playing the game I guess. I knew this was going to be a problem. Maybe in an update not too far away. ;)

But not that much of a prob as the open source drivers work fine for what my wife wants to do with her new laptop. Cheers....

All suggestions welcome, naturally ...

** Actually, please check this out ... :

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Tried it but can't open the file or install anything. More thinking ...

---

