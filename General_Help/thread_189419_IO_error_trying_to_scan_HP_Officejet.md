---
title: "IO error trying to scan HP Officejet"
date: 2006-06-05
forum: General Help
---

### Post by danielph on 2006-06-05
Hi,

Can someone help with a scanning problem? The scanner is detected, but when I try an aquire an image it either "fail to allocate image memory" (xsane) or "IO Error" (quiteinsane). 

The scanner makes a few noises and once it did a paper feed, but that didn't really do it for me.

Here are a few outputs and thanks.

scanimage -L
```
device `hpaio:/par/OFFICEJET_PRO_1170C_SERIES?device=/dev/parport0' is a hp OFFI CEJET_PRO_1170C_SERIES multi-function peripheral
```
dmesg output
```
[4294683.753000] parport: PnPBIOS parport detected.
[4294683.753000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]

```
```
[4298401.400000] ppdev0: registered pardevice
[4298401.441000] ppdev0: unregistered pardevice
[4298425.045000] ppdev0: registered pardevice
[4298425.062000] ppdev0: negotiated back to compatibility mode because user-space forgot
[4298425.062000] ppdev0: unregistered pardevice
[4298425.461000] ppdev0: registered pardevice
[4309138.532000] ppdev0: negotiated back to compatibility mode because user-space forgot
[4309138.532000] ppdev0: unregistered pardevice
```

tail -f /var/log/messages
```
Jun  5 12:39:18 localhost python: hpssd [WARN] Inrecognized URI: parallel:/dev/l p0

```:-\"

---

### Post by danielph on 2006-06-23
bump

---

### Post by danielph on 2006-09-24
This is the only thing I havent managed to get working on Ubuntu so I going to bump even if it has been a while, I would really like to get some suggestions to finding a solution here. Thanks

---

