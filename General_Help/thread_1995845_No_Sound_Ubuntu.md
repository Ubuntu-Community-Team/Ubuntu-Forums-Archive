---
title: "No Sound Ubuntu"
date: 2012-06-03
forum: General Help
---

### Post by rmaunus on 2012-06-03
Hi, I've been having a problem with sound today. It started off in Ubuntu 11.10. I tried to turn off the sound coming from my laptop's speakers so it would only come out of the speakers I had plugged in. When I went to change the hardware settings, all the sounds stopped. Sounds will not play. When I tried to play music on a player or play a video on YouTube, the video or song is sped up, it skips 2 or 3 seconds for every 1 second that goes by, and no sound. I couldn't fix it by putting the sound back to its regular settings. So I decided to update to 12.04, and I still have the same problem. Can anyone help me?

---

### Post by rmaunus on 2012-06-03
Any help?

---

### Post by idoitprone on 2012-06-03
> **rmaunus said:**
> Any help?

there is a 24 hr bump rule

paste output of 
> lspci -nnk
aplay -l

this will aleast tell people of your card so they can start helping

i am not that good at debuging the piece of crap that is called alsa

---

### Post by whit on 2012-06-20
I'm having the same problem after an upgrade from 11.04 to 12.04. No sound, and videos skip ahead as fast as they can be downloaded. Tried installing VLC to see if that would resolve the problem, but the problem remains exactly the same.

Just in case it's useful, here's relevant parts of lspci -nnk
> 
 01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series] [1002:68d9]
        Subsystem: PC Partner Limited Device [174b:e142]
        Kernel driver in use: radeon
        Kernel modules: radeon
 01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series] [1002:aa60]
        Subsystem: PC Partner Limited Device [174b:aa60]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel

and aplay -l 
> 
 **** List of PLAYBACK Hardware Devices ****
 card 0: SB [HDA ATI SB], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 card 0: SB [HDA ATI SB], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

