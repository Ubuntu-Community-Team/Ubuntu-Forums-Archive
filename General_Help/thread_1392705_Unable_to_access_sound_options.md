---
title: "Unable to access sound options"
date: 2010-01-28
forum: General Help
---

### Post by Enigmapond on 2010-01-28
I had some horrible issues with pulseaudio so I deleted it and am using alsa. This is working well, however there are two issues now.

1. I am unable to access the sound options on System/Preferences/Sounds. When I click the icon it states "waiting for the sound system to respond" and that's where is stays.

2. I lost the volume control in gnome when pulse was deleted. I can see it in the system monitor as "sleeping" and when I try to initiate it in the terminal, I get the same response "waiting to the sound system to respond". Did I delete something I shouldb't have when deleting pulse? I followed the tutorial on it and did nothing on my "intuition".

Any help you be appreciated.

---

### Post by Enigmapond on 2010-01-28
:confused:

---

### Post by john_spiral on 2010-01-28
post the results from the following command:

lspci

should give more info on your sound hardware

---

### Post by Enigmapond on 2010-01-28
Thank you for your response!


00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:0b.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
02:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI[/code]

---

### Post by john_spiral on 2010-01-28
search the forum for all or part of:

Cirrus Logic CS 4614/22/24/30

I'm sure there must be people out there with the same problem

---

### Post by Enigmapond on 2010-01-28
Well if they are they keep it a secret. I searched for a week prior to posting this...I have no idea/ I guess I should count my blessings that I actually HAVE sound.....

Thanks Anyway............

---

### Post by john_spiral on 2010-01-29
try google Cirrus Logic CS 4614/22/24/30 & gnome & linux

---

### Post by Enigmapond on 2010-03-22
This is technically solved...I switched back to Jaunty...sound works like a champ..always did..:)

---

