---
title: "sound card trouble: sound group permissions?"
date: 2009-11-16
forum: General Help
---

### Post by ktronicon5 on 2009-11-16
Hello, I just installed Ubuntu 9.10 on my computer (not an upgrade) and am not getting any sounds out of my sound card. System seems to recognize it, but no sound. I tried to follow the community help page ([https://help.ubuntu.com/community/So...20Installation](https://help.ubuntu.com/community/So...20Installation)) but got stumped on a few things: it says to check that i'm "in the sound group in etc/groups" and this is what I got:


]keith@keith:~$ sudo adduser keith sound
adduser: The group `sound' does not exist.

Also how do I find out the name of my soundcard driver?
thanks,
k

---

### Post by ktronicon5 on 2009-11-16
Ok I see my mistake and have added my username to the sound group.

But still no sound

I should mention that it's a multi-in multi-out sound card: 
Hoontech STA DSP 24 which shows up as "0 snd_ice1712".

In "sound preferences" the output is shown as "dummy output" 

any ideas?
thanks
k

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
I found this in a pulseaudio howto on this forum. >  Originally Posted by rod40cool  View Post
Hey anyone out there having difficulty trying to get Pulseaudio working with a hardware playback device that uses ICE1712 (as displayed when you run the command "aplay -l", there is a bug I have found which seems to affect all cards using this chipset.

For example my card is card 0: H71 [Hoontech STA DSP24 Media 7.1], device 0: ICE1712 multi [ICE1712 multi] but according to this bug other cards such as M-Audio type cards are affected too.

There is a manual workaround listed in this bug.
[https://bugs.launchpad.net/ubuntu/+s...io/+bug/178442](https://bugs.launchpad.net/ubuntu/+s...io/+bug/178442)
There is a posting about an M-Audio Delta 44 card...
[https://bugs.launchpad.net/ubuntu/+s...442/comments/8](https://bugs.launchpad.net/ubuntu/+s...442/comments/8)

I have found that this workaround works for my card too.

If it helps people I have included the steps I made to get my ICE1712 type card working in pulseaudio.

In my example you will need to replace the "H71" with whatever the device says when you run
Code:

asoundconf list

By editing this file,
Code:

gksudo gedit /etc/pulse/default.pa

and adding the following lines at the end, I now have a working pulseaudio in 8.10 64 bit.

Code:

# Workaround for MAudio Audiophile 
# [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7)
# Added comment rod40cool - (STA Audio Media 7.1 card uses same ICE1712 driver)
# Added comment rod40cool - Run command "asoundconf list" to determine what to add after "device=hw:????"
# Added comment rod40cool - Make sure after pasting that there are only 2 lines below starting each with "load-module module..." 
load-module module-alsa-sink sink_name=H71_out device=hw:H71 format=s32le channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7
load-module module-alsa-source source_name=H71_in device=hw:H71 format=s32le channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9

I hope this helps someone who is trying to get pulseaudio running for a ST Audio Media 7.1 or M-Audio Delta card or in fact any card that uses the ICE1712 driver.

Cheers Hope it helps

---

### Post by ktronicon5 on 2009-11-20
Thanks for the info! 
however the terminal does not seem to recognize the command 

asoundconf list

that's to check if there's any conflicts with the sound card? 
i'm very new to this so maybe i'm doing it wrong...

here's what i get with the aplay command: 

```
keith@keith:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 1: ICE1712 consumer [ICE1712 consumer]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DSP24 [Hoontech SoundTrack Audio DSP24], device 2: ICE1712 consumer (DS) [ICE1712 consumer (DS)]
  Subdevices: 6/6
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
```


also the links with the bug info can't seem to be found...maybe i'll try back later?
thanks,
k

---

### Post by ktronicon5 on 2009-11-21
Here are some updates on the situation, if anyone can help:

checked for conflicts with on-board sound card: it was already disabled in bios.

no "slmodemd" process running.

sound preferences lists a "dummy output:" not sure what this means. 

in alsamixer, there is a place for my output port, but no level meter attached to it. i think this is normal but not sure. it is default set to "pcm out," and changing it has no effect. 

i'm pretty sure i'm using karmic's kernel, ... how do i check? i tried re-installing pulse but it told me i was using the latest version. 

i would like to try the workaround Sin sent out but the link doesn't work.
can anyone please help?

thanks,
k

---

