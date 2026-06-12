---
title: "no HDMI audio &amp; no multitasking"
date: 2010-11-16
forum: General Help
---

### Post by lifzunik on 2010-11-16
Hi

I am big fan of Ubuntu and presently doing a lot of research on switching over to Ubuntu from Windows environment. Very new to Ubuntu...

First things first
My desktop basic hardware specs

Motherboard: GIGABYTE MA790XT-UD4P
CPU: AMD PHENON 545
GPU: NVIDIA GT240 (1GB)
RAM: 4GB
POWER: 650W
HDD: 1TB

I am using Win 7 64bit and installed Ubuntu 10.10 64bit
Ubuntu installation went smooth and it got updated...

Everything is fine except couple of things

1. No audio output from HDMI. 
2. No Multitasking.

I will elaborate the above issues

1. My comp display is my LCD TV which is connected by HDMI cable, usually I get sound from TV speakers when I use Win 7, however in Ubuntu there is option to select the sound output by HDMI but even though after selecting nothing happens...

2. Whenever I am to listen to music in Ubuntu and if I am doing some other work like copying files or opening multiple files or burning DVD's, music gets stuck or it plays pause by pause...so multitasking problems...

How to solve above issues???

---

### Post by papibe on 2010-11-16
In order to use audio over hdmi you need to install the nvidia driver. Go to System -> Administration -> Hardware Drivers and select the nvidia driver (version current [recommended]). It maybe required to reboot to take effect, but I'm not sure. 

After the driver is working, go to either System -> Preferences -> Sound or to the speaker icon on the upper bar. There, look in the Hardware and Output tabs to select nvidia for audio hardware, and hdmi as output.

I hope it helps.

---

### Post by lifzunik on 2010-11-16
Installed the Nvidia drivers but nothing works

---

### Post by papibe on 2010-11-16
Could you post the result of this command?
```
$ aplay -L
```
Regards.

---

### Post by lifzunik on 2010-11-18
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions

---

### Post by papibe on 2010-11-18
> **lifzunik said:**
> 
..
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
...


It looks good. Are you able to select the Nvidia HDMI device on your sound preferences?

Regards.

---

### Post by axept on 2010-11-18
You can try this:

1: Select HDMI Output in the sound preferences
2: Go to terminal, run alsamixer
3: Go to the right to you find S/PDIF
4: Try to mute/unmute them, maybe one must be unmuted. Just try. You have to play a video or a song when you try this. When you get sound, exit alsamixer (Esc).
5: run sudo alsactl store

This worked for me with a Nvidia card.

Just remember to play a song or viedo when you try this..

---

### Post by lifzunik on 2010-11-18
> **papibe said:**
> It looks good. Are you able to select the Nvidia HDMI device on your sound preferences?

Regards.


I am able to select the HDMI device but no sound yet...

---

### Post by lifzunik on 2010-11-18
I don't know how to mute or unmute however I got this when I tried alsamixer

---

### Post by papibe on 2010-11-18
When you're executing alsamixer is using the default sound card which is the motherboard (you can see it on the upper left: HDA ATI SB)

In order to adjust the level on the nvidia card you need to run:
```
$ alsamixer -c nvidia
```
Try NVidia, or NVIDIA if it doesn't work with lowercase.

Regards.

---

### Post by onaridge on 2010-11-19
I don't know if this will help but I had to turn off my internal audio. Once I did that, the HDMI sound worked. I went to sound preferences, hardware, and under: choose a device to configure, I selected "off" in the internal audio profile. When I want to listen to audio again, I have to select analog stereo duplex for that internal audio.

---

### Post by lifzunik on 2010-11-19
> **onaridge said:**
> I don't know if this will help but I had to turn off my internal audio. Once I did that, the HDMI sound worked. I went to sound preferences, hardware, and under: choose a device to configure, I selected "off" in the internal audio profile. When I want to listen to audio again, I have to select analog stereo duplex for that internal audio.


Idea was good but did't worked...:(

---

### Post by lifzunik on 2010-11-19
I tried this but not giving any output

alsamixer -c nvidia

---

### Post by lifzunik on 2010-11-19
Feeling like Win 7 is much better...but I don't want to give up

---

### Post by theSuperman on 2010-11-19
I have a new 2010 Macbook that does HDMI through MiniDisplayport, and I am having the same kind of troubles. I finally got static (better than nothing I guess) to come out of the TV speakers, and some really choppy audio (on for a split second, off for a few seconds).  I got this by going into alsamixer and unmuting  S/PDIF 2. This is when I have Digital Stereo (HDMI) selected as a profile. 

So I am under the impression its a problem with Alsa.

---

### Post by lifzunik on 2010-11-19
I got this when I hit F6 in alsamixer, I as able to select the Nvidia card...but I don't know what to do???

---

### Post by luca64bit on 2010-11-19
same. did you solved it?

---

### Post by axept on 2010-11-19
> **lifzunik said:**
> I got this when I hit F6 in alsamixer, I as able to select the Nvidia card...but I don't know what to do???


When you find the S/PDIF things I wrote above, you hit "m" to mute/unmute.
But you have to select the HDMI output in Sound preferences.

---

### Post by luca64bit on 2010-11-19
> **axept said:**
> When you find the S/PDIF things I wrote above, you hit "m" to mute/unmute.
But you have to select the HDMI output in Sound preferences.
 
Thanks for the response. I did what you said, but still no sound. I can't change the levels with the up/down arrow

---

### Post by onaridge on 2010-11-19
Try downloading the latest ALSA drivers from Unstable PPA?

---

### Post by axept on 2010-11-19
> **luca64bit said:**
> Thanks for the response. I did what you said, but still no sound. I can't change the levels with the up/down arrow

Okay, I didnt change the level on S/PDIF, I just muted/unmuted them.. nothing else.. I think I have 2 unmuted and one muted, don't remember, its on mye HTPC (ASRock ION).

But anyway, I hope you find something that works for you!!:popcorn:

---

### Post by lifzunik on 2010-11-20
Nothing worked for me to get sound from HDMI, I am done now and I switched back to Win 7 and everything works fine... life is become easy now....after all the codes and checking with Ubuntu, alsamixer, muting and unmuting...end of the day its waste of time...

---

