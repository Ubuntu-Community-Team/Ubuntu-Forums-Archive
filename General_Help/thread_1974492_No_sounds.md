---
title: "No sounds"
date: 2012-05-06
forum: General Help
---

### Post by tanveerahmed2k8 on 2012-05-06
Hi my mother board is 
gigabyte A75-D3H 
it is new i just install this OS
and i have no sound I use
"HDMI" from motherboard to my 24" 1080p monitor which has built in speakers and works perfectly fine in windows
I dont know the problem why it not work in ubuntu tho
can you please help me out
yesterday i had this ubuntu guy from the IRC look at it and he couldn't find the problem
also i have tried
to aplay /usr/share/sounds/alsa/Front_Center.wav
but stil no sound


edit:
 i typed in
lspci -v | grep -A7 -i "audio"

i got back
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
        Subsystem: Giga-byte Technology Device 1714
        Flags: bus master, fast devsel, latency 0, IRQ 53
        Memory at fe01c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
        Subsystem: Giga-byte Technology Device a102
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

---

### Post by Shadius on 2012-05-06
> **tanveerahmed2k8 said:**
> Hi my mother board is 
gigabyte A75-D3H 
it is new i just install this OS
and i have no sound I use
"HDMI" from motherboard to my 24" 1080p monitor which has built in speakers and works perfectly fine in windows
I dont know the problem why it not work in ubuntu tho
can you please help me out
yesterday i had this ubuntu guy from the IRC look at it and he couldn't find the problem
also i have tried
to aplay /usr/share/sounds/alsa/Front_Center.wav
but stil no sound


edit:
 i typed in
lspci -v | grep -A7 -i "audio"

i got back
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
        Subsystem: Giga-byte Technology Device 1714
        Flags: bus master, fast devsel, latency 0, IRQ 53
        Memory at fe01c000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

--
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
        Subsystem: Giga-byte Technology Device a102
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

Hi, perhaps this thread will help:
[http://ubuntuforums.org/showthread.php?t=1800773]("http://ubuntuforums.org/showthread.php?t=1800773")

Sorry I couldn't provide a full answer. Good luck.

---

### Post by tanveerahmed2k8 on 2012-05-06
Never mind the HDMI audio does not work , but external speakers do

---

### Post by kimme on 2012-05-06
Tried un-muting the HDMI with the cms "alsamixer" in terminal?

---

