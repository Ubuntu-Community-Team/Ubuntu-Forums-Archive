---
title: "More HDMI issues"
date: 2010-08-10
forum: General Help
---

### Post by bprins on 2010-08-10
After solving the problems:
- HDMI device not recognized in aplay -l
- upgrading Alsa to 1.0.23
- multiple HDMI devices installed

I now have an ubuntu laptop where 

1) aplay -l outputs
```

bas@ubuntu-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

2) cat /proc/asound/version outputs:
```

bas@ubuntu-lt:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Aug 10 2010 for kernel 2.6.32-24-generic (SMP).

```

3) cat /etc/modprobe.d/sound.conf outputs
```

bas@ubuntu-lt:~$ cat /etc/modprobe.d/sound.conf
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel enable_msi=0 probe_mask=-1,4

```

4) I unmuted my HDMI device in alsamixer (alsamixer -C 1)

So with full confidence, I took my laptop to my TV and connected HDMI cable and switched to HDMI input. 

I tried XBMC -> nothing, no sound, just video.
I tried aplay -D plughw:1,3 test.wav -> nothing, no sound
I tried aplay -D plughw:0,0 test.wave -> sound on my laptop

Who can help me any further on this horrible search to the solution. What else can I manipulate?

Btw, just to **** me off more, I booted to Win7, just to check if it worked. I never touched Win7 before. Sound and video over HDMI works. Out of the box. Like.. ffs! :)

Hope you guys can get me any further.

Epic thanks in advance.

Bas

---

### Post by dcstar on 2010-08-11
> **bprins said:**
> After solving the problems:
- HDMI device not recognized in aplay -l
- upgrading Alsa to 1.0.23
- multiple HDMI devices installed
........

System-Preferences-Sound-Hardware.

---

### Post by bprins on 2010-08-11
What should I change there?

I've got 2 devices to configure under the hardware tab.
- hdmi digital stereo (my nvidia gt220)
- analog stereo (my integrated sound card)

both have the correct profile. seems fine with me.

---

