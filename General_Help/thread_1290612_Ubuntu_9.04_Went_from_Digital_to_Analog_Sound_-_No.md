---
title: "Ubuntu 9.04 Went from Digital to Analog Sound - No sound issue"
date: 2009-10-13
forum: General Help
---

### Post by ZeroPM on 2009-10-13
Hello fellow Ubu's.. 

So I spent all the time getting Digital Sound to work which I did get working just fine. However I have since moved stuff around and I am now using normal cheap 2 speakers for my system... Upon switching I have lost all sound. I tried to go to the sound properties and messed with far to many options :popcorn:... You all know how that goes but no luck in getting sound. I imagine its because of the switch from digital back to analog but not sure how to fix. 

Hopefully someone can help and even more so hopefully someone has one of those cool little console text strings I can enter and have it fix itself basically. Those text strings can sometimes do some amazing things all at once. 

So ill be messing with settings in the mean time :confused:

**Update** 
- Nothing seems to be muted
- Left everything on auto detect
- Tried unplugging then replugging
- Made sure speakers were on and turned up :P 
- Tried aplay -l and it does seem to reconize my sound

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

- I tried another command and got this:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller
 (rev 02)
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fb100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


- Now that I think about it, I might have had to edit a file manually to get digital audio to work which probably has to be undone to get my sound to work. Dunno at this point. Everything seems to be detected and working just no sound. 



Still no sound however.

---

