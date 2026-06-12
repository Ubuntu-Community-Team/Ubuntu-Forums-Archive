---
title: "Built-in Microphone constant static/crackle and low volume"
date: 2012-08-28
forum: General Help
---

### Post by wakary on 2012-08-28
I'm using Lubuntu 12.04 on an Eee-PC with HDA intel soundcard.
The microphone works perfect in WinXP (dualboot, same machine).

The crackling/static is present in Skype, Audacity.
And the volume is also very low, I have to boost the mic in PulseAudio Volume control to have a conversation on skype, but this also increases the volume of the static. 

When I use an external mic(from the headset) the crackling/static is much worse(again the headset mic works perfectly in Win XP same machine)

---

### Post by Mark_in_Hollywood on 2012-08-28
We can't tell what hardware you have, but if you know how to open the 'terminal', do so and type:


alsamixer


the terminal will return something like the screenshot I've attached to this reply. Enlarge the terminal window so that you can read all that is there. If you have front AND rear microphones, play with that. I'm sorry I cannot be of more help immediately. If using the alsamixer doesn't help, please post your system hardware by make (HP) and model (WebCam #123). It maybe be needed to help you resolve the problem.

Also, when using Skype, open the option/tools (or is that tools/options) and see if the microphone is set to your microphone use use for communications.

Please use the "Thread Tools" to mark this thread as "Solved" after the resolution.

---

### Post by wakary on 2012-08-29
> **Mark_in_Hollywood said:**
> We can't tell what hardware you have, but if you know how to open the 'terminal', do so and type:


alsamixer


the terminal will return something like the screenshot I've attached to this reply. Enlarge the terminal window so that you can read all that is there. If you have front AND rear microphones, play with that. I'm sorry I cannot be of more help immediately. If using the alsamixer doesn't help, please post your system hardware by make (HP) and model (WebCam #123). It maybe be needed to help you resolve the problem.

Also, when using Skype, open the option/tools (or is that tools/options) and see if the microphone is set to your microphone use use for communications.

Please use the "Thread Tools" to mark this thread as "Solved" after the resolution.

Alsamixer didn't help. About skype, in sound settings it says I have pulseaudio running, to change settings use pulseaudio volume control. (I used pulseaudio to no avail ex: switched from 'built in audio analog stereo' to 'monitor of built in audio analog stereo' and other options but nothing worked)

About the hardware:
Card: HDA Intel 
Chip: Realtek ALC269
 
At the F2 menu:
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.

/proc/asound/cards 
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xf7eb8000 irq 43

/proc/asound/devices
1:        : sequencer    
2: [ 0- 0]: digital audio playback
3: [ 0- 0]: digital audio capture
4: [ 0- 0]: hardware dependent
5: [ 0]   : control
33:        : timer 

/proc/asound/timers 
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE     
P0-0-1: PCM capture 0-0-1 : SLAVE

/proc/asound/pcm 
00-00: ALC269 Analog : ALC269 Analog : playback 1 : capture 1

edit: I tried to boost mic just the left side or just the right side, or the capture option.

---

### Post by Mark_in_Hollywood on 2012-08-29
I have not re-installed Skype in Precise Pangolin (v. 12.04). No particular reason, except for lack of use. I cannot remember the place in Skype where you can see what is used for input/output. But as your sound is a mess in both Sk & another, please have a look at:

[http://ubuntuforums.org/showthread.php?t=1491297&highlight=alsa](http://ubuntuforums.org/showthread.php?t=1491297&highlight=alsa)

The wrong hardware device had been defaulted and sound fixed on change of device.

Also, FYI, some users of Realtek ALC269 report a bug as: 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014105](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1014105)

---

