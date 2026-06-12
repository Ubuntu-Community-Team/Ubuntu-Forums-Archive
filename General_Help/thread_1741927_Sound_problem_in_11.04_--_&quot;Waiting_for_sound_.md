---
title: "Sound problem in 11.04 -- &quot;Waiting for sound system to respond&quot;"
date: 2011-04-28
forum: General Help
---

### Post by msp3k on 2011-04-28
Hi gurus,

BACKGROUND: 
I have an iMac9,1 with the following sound card:
```
# lspci | grep Audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The machine has been running Ubuntu-9.10, under which version the sound never worked.  I have tried all the howto posts by others that I could find, compiled my own version of alsa, and tried snd-hda-intel model=(mb5|mbp5|mbp3|mac24|imac24|auto), all to no avail.

TODAY:
Today I installed 11.04, and was excited when the machine booted up and played the drum-boot-up-sound.  My excitement was short-lived, however, as the sound still doesn't seem to be working properly.

1) If click on the volume notification icon, the drop-down window tells me that the volume is at 0%, and I cannot move the volume slider.

2) If I click on the volume notification icon and select "Sound Preferences..." (which I believe runs the program gnome-volume-control), I get a small pop-up window saying "Waiting for sound system to respond".  This window will stay up, waiting, until the cows come home.

3) BUT -- if I open a terminal window and type: ```
aplay /usr/share/sounds/purple/alert.wav
``` Then the sound file plays just fine.

For some reason, however, the gnome controls don't seem to be able to talk to the sound card.

Again, I have tried each of the following, in turn:
```

options snd-hda-intel model=mb5
options snd-hda-intel model=mbp5
options snd-hda-intel model=mbp3
options snd-hda-intel model=mac24
options snd-hda-intel model=imac24
options snd-hda-intel model=auto

```

And since the version of alsa that ships with 11.04 is now newer than the version in any of the howto posts I've seen in the past, then I would have expected one of the above settings to work.

A little more information:
```

# uname -a
Linux canis 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
# lspci | grep Audio
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
# amixer -c0
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 27 [87%] [6.00dB] [off]
  Front Right: Playback 27 [87%] [6.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
root@canis:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

```

---

### Post by gurudev1000 on 2011-05-03
I have a new install of 11.04 too. Sound worked 'fine' until this fresh install whereing I don't get any control through the GUI sound preference. Clicking on sound pref. loads up 'waiting for sound device to respond'. I had to increase the alsa mixer sound through terminal to get a bit more decent volume.

Otherwise, the sound quality right now especially (though it always has been for me in older versions) is substandard in comparison to Windows. Surprising this problem is not making news if even two users are facing it who might not have had problems with 10.10.

All the Best again Ubuntu creators. Hope you get better with each update.

---

### Post by cake nom nom on 2011-05-10
Same problem.. I'm going to try to reboot see if that works although I don't consider that a fix.. more like a nuisance sigh, It gets quite frustrating how rudimentary Ubuntu *STILL is*.
 I cant grasp the logic or even begin understand the need to come out with these new releases..........
such as 11.04 because Ubuntu 10.10 still has so many unsolved problems 
In my opinion, 

They should make one  version, and perfect it. They make sure it's flawless. you know? GOOD, WORKING, and STABLE before making a new half ***'d one.. with some of the same problems and more new ones....... These deadlines of April and October are silly.

Shouldn't start something else until you finish what you've started.....

---

### Post by Chronin on 2011-05-24
I have a similar problem with sound. When Ubuntu starts up, the startup sound begins then gets cut off as the desktop loads. The volume indicator doesn't work and when I click on it, I get the "waiting for sound system to respond"

It usually takes several restarts for it to work. Anywhere from a couple to 10+ reboots. I try to avoid restarting but sometimes I need to boot into Windows for work. I have been running a few versions on this computer for about 2 years with no problems until I upgraded to 11.04.

---

### Post by 5149.5 on 2011-05-24
> **cake nom nom said:**
> Same problem.. I'm going to try to reboot see if that works although I don't consider that a fix.. more like a nuisance sigh, It gets quite frustrating how rudimentary Ubuntu *STILL is*.
 I cant grasp the logic or even begin understand the need to come out with these new releases..........
such as 11.04 because Ubuntu 10.10 still has so many unsolved problems 
In my opinion, 

They should make one  version, and perfect it. They make sure it's flawless. you know? GOOD, WORKING, and STABLE before making a new half ***'d one.. with some of the same problems and more new ones....... These deadlines of April and October are silly.

Shouldn't start something else until you finish what you've started.....

I absolutely agree. There are bugs in 11.04 that have been around since 9.04.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Can you guys try creating a 10.10 and see if you can replicate this issue in 10.10 for me?

---

### Post by 5149.5 on 2011-05-24
> **linuxinstalledfromhdd said:**
> Can you guys try creating a 10.10 and see if you can replicate this issue in 10.10 for me?

Sorry, but I've gotta ask why?

---

### Post by linuxinstalledfromhdd on 2011-05-24
a somewhat baseline comparison between natty bugs and a system that I know is stable? 

I don't mind helping someone that -knows- they are guinea pig, but I am not going to waste my time debugging the debugging problems of a latest version of Ubuntu if I can help it.  Does that make sense? I think they want systems that just works... not be beta testers..  but I could be wrong. :)

---

### Post by 5149.5 on 2011-05-24
> **linuxinstalledfromhdd said:**
> a somewhat baseline comparison between natty bugs and a system that I know is stable? 

I don't mind helping someone that -knows- they are guinea pig, but I am not going to waste my time debugging the debugging problems of a latest version of Ubuntu if I can help it.  Does that make sense?

Sorta yes and sorta no. If you google "ubunntu 10.10 sound problem", there are plenty of posts to look at that are just like the current crop of complaints. Try the the same thing with 10.04 and the complaints all look the same as well. I have now come to realize that ubuntu never stops working on the next release and attempts to clean up all of the bugs on the current release. We're all guinea pigs running our own version of beta.

---

### Post by linuxinstalledfromhdd on 2011-05-24
I don't mind helping to debug problems, but I want to remove any doubt that it is a new bug in natty itself or just something that is purely hardware related.  As much info as possible helps to make that kind of determination of course.  I'm stuck in 10.10 for now myself, so I understand how they feel too. :)

---

### Post by Chronin on 2011-05-25
> **Chronin said:**
> I have a similar problem with sound. When Ubuntu starts up, the startup sound begins then gets cut off as the desktop loads. The volume indicator doesn't work and when I click on it, I get the "waiting for sound system to respond"

It usually takes several restarts for it to work. Anywhere from a couple to 10+ reboots. I try to avoid restarting but sometimes I need to boot into Windows for work. I have been running a few versions on this computer for about 2 years with no problems until I upgraded to 11.04.

**Update**: I deleted everything in the .pulse folder in home and it seems to be working fine now. It seemed to work for a few restarts but it was just a coincidence.

---

### Post by tanaya chaudhuri on 2011-05-25
may be you could try [COLOR=navy]**[SIZE=4][B]Comprehensive Sound Problem Solutions Guide** v0.5e [/SIZE][/B][/COLOR]at _[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_. I did, and my sound problem was solved big times. I am quite new in linux... ubuntu 10.04 LTS user for only 5 months now, but my sound problem was solved with the help of this guide. Hope it works for you too. Good luck. :P

---

### Post by chinmaya_n on 2011-06-25
Check this 

[http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html#more-5870](http://www.ubuntugeek.com/ubuntu-10-04-tip-how-to-fix-waiting-for-sound-system-to-respond-problem.html#more-5870)

---

