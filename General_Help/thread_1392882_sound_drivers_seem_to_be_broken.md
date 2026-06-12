---
title: "sound drivers seem to be broken"
date: 2010-01-28
forum: General Help
---

### Post by Stronze on 2010-01-28
i tried finding a thread already on this issue but none seem to what i need to solve this issues.
tried #ubuntu but people busy or no one on that knows how to handle this problem.

ISUES
Movie player - sound is good sometimes gets choppy
Skype - hear static - person called hears nothing but can hear dailed numbers when i click em.
youtube type videos - breaks sound, reboot required

WHILE using movie player,youtube videos will play static but wont break sound. even if a movie is paused. if attempt youtube video without movie player open, movie sound is broke.

im deployed to iraq and want to use skype to call home and talk to family.
issues started before skype install but since i need skype, i can no longer ignore this 

DISTRO - ubuntu 9.04


[LIST]
[*]sudo aplay -l
[/LIST]
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[LIST]
[*]lshw
[/LIST]
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel


after reboot. 
dont know why those 3 OSS are identical and 1 has a different result.
after sound crashes i have different results. only one plays the beep rest are static or error message
          
SYSTEM>PREFENCES> SOUND        
                            ~SOUND EVENTS; SOUND PLAYBACK~

[LIST=1]
[*]Autodetect - static
[*]HDA Intel ALC268 Digital  (ALSA) - nothing
[*]HDA Intel ALC268 Analog (ALSA) audiotestsrc wave=sine freq=512!
[*]                                                audioconvert! audioresample ! gconfaudiosink:
[*]                                                Could not open audio device for playback.
[*]HDA Intel ALC268 Analog (OSS)  strong steady beep
[*]HDA Intel ALC268 Analog (OSS)  strong steady beep
[*]HDA Intel ALC268 Analog (OSS)  nothing
[*]A.L.S.A. ~~~~~~~~~~~~~~~ static
[*]O.S.S. ~~~~~~~~~~~~~~~~ strong steady beep
[*]PulseAudio Sound Server            Static
[/LIST]
i tried to give all info i could think of with my limited knowledge

---

### Post by Stronze on 2010-01-29
bump

---

### Post by Stronze on 2010-01-29
since nobody cared to at least point me in the right direction, i tried this guide out
[http://ubuntuforums.org/archive/index.php/t-878608.html](http://ubuntuforums.org/archive/index.php/t-878608.html)

and now sound is complete gone.
only thing that i couldnt get was pop up the config screen like it said it would.
 
and terminal displayed this at the end

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

Remove Folder.....
./install: 108: alsaconf: not found

---

### Post by Stronze on 2010-01-30
well i fixed sound by removing ALL sound drivers and reinstalling ALSA.


[LIST]
[*]sudo apt-get install module-assistant
[*] sudo m-a update
[*] sudo m-a prepare
[*] sudo m-a a-i alsa
[/LIST]
those commands got it working again.
only issue i have now is i can hear sound in the headset but not in the laptop speakers.

---

