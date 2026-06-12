---
title: "HDMI for sound not working"
date: 2012-06-11
forum: General Help
---

### Post by famebu on 2012-06-11
I have my monitor and tv setup with twin view and am trying to use the hdmi to get sound though my tv but nothing I do seems to work.
The master channel is set to hdmi but still doesn't work it will still only use my speakers. I have tried setting every other thing is the sound options to hdmi and it still doesn't work.
The only way I am able to get sound via hdmi is to use vlc and select hdmi as audio device and it works just fine then but i am trying to watch a movie on youtube and can't do that. 

I have never setup dual monitors before so I am probably just missing something, thank you for the help!

---

### Post by steeldriver on 2012-06-11
I had similar symptoms on a recent HTPC build (HDMI sound via vlc but not flashplayer) - eventually solved by setting a default pulseaudio device via /etc/asound.conf (you can also try it in ~/.asound.rc I think)

```
pcm.!default {
    type hw
    card 0
    device 3
}

```

where the card and device #s are your HDMI outputs (from aplay - L, or look at the working config under vlc -> Tools -> Preferences -> Audio)

Just something to try

---

### Post by Cariboo1938 on 2012-10-08
Hello,

similar problem with 
HP pavilion g6 under Ubuntu 12.04-64bit 
Laptop connected via HDMI cable to TV. 
Video output OK but no sound using vlc as media player. 
What exactly would I have to do when you say> solved by setting a default pulseaudio device via /etc/asound.conf (you can also try it in ~/.asound.rc I think) I would appreciate if you could give me more detailed info as I'm not a software expert? 
I have attached the terminal output of command```
aplay -L
```
OR
terminal output for *cat /proc/asound/cards*
> jg-laptop@JG-Laptop:~$  cat /proc/asound/cards 
0 [Generic ]: HDA-Intel - HD-Audio Generic HD-Audio Generic at 0xf0544000 irq 44 
1 [Generic_1 ]: HDA-Intel - HD-Audio Generic HD-Audio Generic at 0xf0540000 irq 16

---

