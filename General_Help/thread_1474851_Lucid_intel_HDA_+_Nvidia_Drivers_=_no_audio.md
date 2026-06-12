---
title: "Lucid intel HDA + Nvidia Drivers = no audio"
date: 2010-05-06
forum: General Help
---

### Post by deadite66 on 2010-05-06
Pulseaudio mixer show program connected and volume bar shows output but no audio is heard.
the nvidia drivers appear to be the problem, uninstalled i hear audio, installed i don't.

any ideas.

```
uname -a
Linux sakura 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
	Subsystem: Device 414c:4760
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at e000 [size=256]
	Region 1: I/O ports at eb00 [size=64]
	Region 2: Memory at ec081000 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at ec082000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
	Subsystem: Device 196e:05cf
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at c0000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at c000 [size=128]
	[virtual] Expansion ROM at 40000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
```

---

### Post by deadite66 on 2010-05-08
tried so far:
updated to latest alsa = no sound
installed latest nvidia drivers from nvidia = no sound
removed pulseaudio = no sound
checked all kind of mixers and sound toggles = no sound
reinstalled karmic = no sound

if i close down gdm i get sound.

its all fubar.

---

### Post by deadite66 on 2010-05-08
i have sound again yay
problem was using a dvi-to-hdmi cable, the tv was expecting audio over hdmi so no sound.
i had to create a custom edid with the audio bit disabled.
[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI](http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI)

---

