---
title: "monitor cycles on-off after boot"
date: 2012-04-04
forum: General Help
---

### Post by jloveless on 2012-04-04
This is a strange one. I have been using 11.10 x64 with an NVidia GE 440 graphics card. All of a sudden, when I first boot to Ubuntu at the Password screen, the monitor cycles on and off. I can continue to enter my PW and after a few minutes it stops cycling and stays on. It almost acts as if it needs to warm up before it will stop cycling. The stranger thing is that it doesn't do this cycle thing if I boot to Win7 (this is a dual boot setup). So, I figured it must be something with Ubuntu so I upgraded to the not yet released 12.04 x64 version. Oops, still cycles the monitor for a few minutes after boot. I replaced the GE 440 with another one I had and tried different cables. No change. I turned off sync to vblank wherever I could find it - no change. Frankly, I didn't expect that to do anything - it was desperation.  

Here are some more particulars on my system:
i7-2600 chip, EGA GEForce 440 graphics card, 28" Hannspree monitor currently using HDMI to HDMI, boot drive is sdb which is an 80 GB Intel SSD. sda is Win7.

Does anyone have any clue what has happened here??

Many thanks if you have a tip for me to try.

Jon

---

### Post by efflandt on 2012-04-04
Are you using **nomodeset** kernel boot parameter?  I discovered that I needed to use that for nvidia in 11.10 even when I did not need to use that in 10.10 with the exact same nvidia driver version.  Apparently in 11.10 nouveau and nvidia need to cooperate, which they cannot do using default KMS (kernel mode setting), but can do as old fashion modules. 

Kernel driver in use: nvidia
Kernel modules: nvidia_current, nouveau, nvidiafb

PS: my GTX 550 Ti is EVGA, the failed GT 430 was a Chinese Galaxie

---

### Post by jloveless on 2012-04-05
Thanks. I tried adding that and it rebooted fine. Now I have to try it when the system has cooled off - like tomorrow AM. I'll let you know how it works out. My failed 440 was a Zotac - very cool looking but took up 2 slots and after a month, didn't work.

Jon

---

### Post by jloveless on 2012-04-05
Well, when I booted this morning all was good until I entered my PW in Ubuntu. As soon as I arrived at the my default screen the flashing started again. It lasted 5 minutes during which time I tried to get a glimpse of the cursor so I could open Thunderbird and sign in. It's a bit like a bad video game really. So, thanks for your idea but my search continues. Any others??

---

