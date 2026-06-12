---
title: "No Sound"
date: 2010-04-03
forum: General Help
---

### Post by indexoutofbounds on 2010-04-03
Recently installed Kubuntu  karmic koala (9.10) and I have no sound other then the startup sound. 

Please help ! 

Thanks

[Specs]
O/S: Kubuntu 9.10 Karmic Koala
Mobo: Asus M3A78-EM

---

### Post by quadproc on 2010-04-03
> **indexoutofbounds said:**
> Recently installed Kubuntu  karmic koala (9.10) and I have no sound other then the startup sound. 


I experienced the same thing and I found that the system volume control had defaulted to MUTED.  Click on the tiny loudspeaker symbol in your top bar and see what it says.  Turn it up and you should get audio.

quadproc

---

### Post by indexoutofbounds on 2010-04-03
Thnx, but that does not seem to be the problem. After I rebooted it prompted me that various audio drivers were removed. When i open System Settings > Multimedia I see 
HDA ATI SB (ALC1200 Analog) is grayed out. I tried downloading the realtek audio driver and doing a manual install (doesnt support auto installs on Ubuntu) to fix it but that didn't do anything - still grayed out.

[Specs]
O/S: Kubuntu 9.10 Karmic Koala
Mobo: Asus M3A78-EM
Video: ATI EAH3450 (using proprietary ATI drivers)
8 GB DDR2 RAM (not relevant but nice to boast about :) )


***** Update *****

Still not working. After some reading I think it is worth noting I am not using the onboard video card but a PCIE card (noted in specs). 


++++++++++++++++++++++++++++++++++++++++++++
 KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Capture: HDA ATI SB (ALC1200 Analog)
[*]Capture: HDA ATI SB (ALC1200 Digital)
[*]Output: HDA ATI SB (ALC1200 Analog)
[/LIST]

---

### Post by lidex on 2010-04-04
The HDA ATI SB sounds like onboard audio. Did you disable it in bios? What is the output of this command:
```
aplay -l
```
That is a terminal command: "Applications>Accessories>Terminal"

---

### Post by indexoutofbounds on 2010-04-04
Thnx for the reply. Yes my sound is onboard, and it should not be disabled in BIOS. 

Output of the command:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

ps: I am very familiar with the konsole lol.

Thanks again

---

### Post by quadproc on 2010-04-04
> **indexoutofbounds said:**
> Thnx, but that does not seem to be the problem. After I rebooted it prompted me that various audio drivers were removed.
OK, that disposes of the easy fix.

There is another thread just above this one which seems to address the same problem.  It is probably worth a read.  It seems that there are many people experiencing the "no sound" problem and it looks like the problem is usually associated with some conflict: hardware, drivers, audio software.

Sorry that I can't help with your problem.

quadproc

---

### Post by indexoutofbounds on 2010-04-04
> **quadproc said:**
> OK, that disposes of the easy fix.

There is another thread just above this one which seems to address the same problem.  It is probably worth a read.  It seems that there are many people experiencing the "no sound" problem and it looks like the problem is usually associated with some conflict: hardware, drivers, audio software.

Sorry that I can't help with your problem.

quadproc


Thanks, can you pls send me the link for that other post ?

---

### Post by indexoutofbounds on 2010-04-04
It works !

Thnx everyone for your help. It would seem downloading the alsa driver from realtek worked. 

(Ps: music sounds even better on linux then windows lol)

---

