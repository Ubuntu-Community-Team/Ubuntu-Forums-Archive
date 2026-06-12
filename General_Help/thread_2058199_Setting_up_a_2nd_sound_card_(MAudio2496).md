---
title: "Setting up a 2nd sound card (MAudio2496)"
date: 2012-09-15
forum: General Help
---

### Post by mrkipp on 2012-09-15
Howdy folks 

Any help with this problem would be very much appreciated. Thanks.

Im currently trying to  setup an maudio 2496 as a 2nd sound device in xubuntu 12.10 with ALSA (no pulseaudio). Ive manged to get M2496 working using the speaker test but im a bit confused on how to config .asoundrc with the results im given from the speaker test.
Heres my system info;-

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Ive run the speaker test;-'speaker-test -c 2 -r 44100 -D hw:1,0' which dosnt output sound however after reading this thread;-
[http://ubuntuforums.org/showthread.php?t=1359022&page=4]("http://ubuntuforums.org/showthread.php?t=1359022&page=4") i tried;-'aplay -v -D plughw:M2496 /usr/share/sounds/alsa/Front_Center.wav' and this gives me sound through the card.

The output of 'aplay -v -D plughw:M2496 /usr/share/sounds/alsa/Front_Center.wav
' results in;-
```
james@Server:~/Desktop$ aplay -v -D plughw:M2496 /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
Plug PCM: Route conversion PCM (sformat=S32_LE)
  Transformation table:
    0 <- 0
    1 <- 0
    2 <- 0
    3 <- 0
    4 <- 0
    5 <- 0
    6 <- 0
    7 <- 0
    8 <- 0
    9 <- 0
Its setup is:
  stream       : PLAYBACK
  access       : RW_INTERLEAVED
  format       : S16_LE
  subformat    : STD
  channels     : 1
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 16
  buffer_size  : 6553
  period_size  : 1638
  period_time  : 34125
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1638
  period_event : 0
  start_threshold  : 6553
  stop_threshold   : 6553
  silence_threshold: 0
  silence_size : 0
  boundary     : 1717829632
Slave: Hardware PCM card 1 'M Audio Audiophile 24/96' device 0 subdevice 0
Its setup is:
  stream       : PLAYBACK
  access       : MMAP_INTERLEAVED
  format       : S32_LE
  subformat    : STD
  channels     : 10
  rate         : 48000
  exact rate   : 48000 (48000/1)
  msbits       : 24
  buffer_size  : 6553
  period_size  : 1638
  period_time  : 34125
  tstamp_mode  : NONE
  period_step  : 1
  avail_min    : 1638
  period_event : 0
  start_threshold  : 6553
  stop_threshold   : 6553
  silence_threshold: 0
  silence_size : 0
  boundary     : 1717829632
  appl_ptr     : 0
  hw_ptr       : 0

```

~.asoundrc looks like this so far (its configured to use alsa with my NVIDIAs HDMI output which works fine);-
```
pcm.!default {
      type hw
      card 2
      device 7
      }
```

Ive had this card working in this setup with pulseaduio but wasnt happy with the sound quality.
Any ideas how i need to config asoundrc to enable sound playback?
Many thanks
James

---

### Post by Chiel92 on 2012-09-21
I have no experience with .asoundrc, but I once got my mAudio fasttrack pro working by selecting it as the default sound card. This could be done in the following file: "/etc/modprobe.d/alsa-base.conf". Have a look here [http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-k-ubuntu-499520/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-you-change-the-default-sound-card-in-k-ubuntu-499520/) , or google around this subject.

Regards

---

### Post by mrkipp on 2012-09-21
Thanks for the reply Chiel92. 

I ended up giving up on this problem as i was wasting to much time on it. I tried all weekend in vain to get it working and in the end resorted to putting win xp back on:cry: 

I think i'll end up putting another distro back on in a few months time but for now im leaving it. Im sick of trying to get this to work. 

Ive bookmarked the link you posted as i think it will be handy for future use.

Thanks again

---

### Post by Chiel92 on 2012-09-22
> **mrkipp said:**
> Thanks for the reply Chiel92. 

I ended up giving up on this problem as i was wasting to much time on it. I tried all weekend in vain to get it working and in the end resorted to putting win xp back on:cry: 

I think i'll end up putting another distro back on in a few months time but for now im leaving it. Im sick of trying to get this to work. 

Ive bookmarked the link you posted as i think it will be handy for future use.

Thanks again

Too bad, but I get your point. Sound on linux can be quite frustrating and time consuming. I'm experiencing soundcard problems as well atm.

---

### Post by mrkipp on 2012-09-23
I installed Win Xp back on my media center and now things are worse. Win Xp can't use my GFX cards HDMI audio](*,). Also i was playing audio through my Maudio card via spidf to my new DAC and was having buffering issues with every track.

One good bit of news is that the new DAC i bought is Linux friendly:D I think i should be able to get it working in xubuntu with alsa via USB. 

I should have just stuck with Linux

---

