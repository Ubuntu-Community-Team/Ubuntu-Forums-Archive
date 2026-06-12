---
title: "how to list audio devices and video devices?"
date: 2009-09-26
forum: General Help
---

### Post by sdowney717 on 2009-09-26
anyone have the command for this?
I want to setup VLC to record a TV signal. It sees the video thru an svideo cable, but I dont hear any audio.
I am using a video audio capture card Adaptec VideOh! AVC-2010 card

which device is it? or is it any of them?

```
scott@scott-desktop:~/Download/bios$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
scott@scott-desktop:~/Download/bios$ 
```

```
[    6.113115] ivtv: Start initialization, version 1.4.1
[    6.113314] ivtv0: Initializing card 0
[    6.113321] ivtv0: Autodetected Adaptec VideOh! AVC-2010 card (cx23416 based)
[    6.113432] ivtv 0000:05:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.403137] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.450181] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[    6.638624] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k 
[    6.717647] cs53l32a 0-0011: chip found @ 0x22 (ivtv i2c driver #0)
[    6.737488] IRQ 18/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    6.738156] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[    6.738297] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[    6.738436] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[    6.738563] ivtv0: Registered device video24 for encoder PCM (320 kB)
[    6.738568] ivtv0: Initialized card: Adaptec VideOh! AVC-2010
[    6.739597] ivtv: End initialization
[    6.800456]   alloc irq_desc for 17 on node -1
[    6.800461]   alloc kstat_irqs on node -1
[    6.800472] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.800525] Intel ICH 0000:00:1f.5: setting latency timer to 64
[    6.813064] EXT4-fs (sda6): internal journal on sda6:8
[    7.172044] intel8x0_measure_ac97_clock: measured 54722 usecs (2636 samples)
[    7.172050] intel8x0: clocking to 48000
[    7.400038] ivtv 0000:05:09.0: firmware: requesting v4l-cx2341x-enc.fw
[    8.101859] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[    8.300177] ivtv0: Encoder revision: 0x02060039

```

---

### Post by sdowney717 on 2009-09-26
ha, 

It is "dev/dsp" for VLC audio when you capture the stream
actually it gives an error, but then you hear the sound. Anyone know what it should be?

this tells how to find devices.

[http://www.linux.org/docs/ldp/howto/Webcam-HOWTO/dev-intro.html](http://www.linux.org/docs/ldp/howto/Webcam-HOWTO/dev-intro.html)

---

