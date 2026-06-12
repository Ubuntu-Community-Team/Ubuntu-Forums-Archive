---
title: "no sound in ubuntu 10.04"
date: 2010-05-25
forum: General Help
---

### Post by Trosky on 2010-05-25
Hello, I just installed ubuntu 10.04 from zero, amd64 version, but there isn't any sound. In alsamixer nothing is on zero level. Alsa and OSS where changed in gstreamer-properties, updated the alsa version but nothing...

Thanks for the help

Some test done:

aplay -l
```

tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC883 Analog [ALC883 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC883 Digital [ALC883 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```

dmesg | grep HDA
```
[    8.225301] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.225325] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.348735] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6

```

lspci -v
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 8249
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fe8f8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: 
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

---

