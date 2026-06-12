---
title: "Mythtv No Sound - no sound card"
date: 2011-07-30
forum: General Help
---

### Post by NertSkull on 2011-07-30
So I upgraded to 11.04.  But I had to install the older (.23-1) version of mythtv (from source) since I didn't upgrade my mythtv backend.

The frontend (on 11.04) turns on and I get picture, but no sound.  I'm trying to get it to go through my digital (IEC958) and I can't figure out what to do.

When I go to the general settings where the sound page is (like I did on 10.10) it doesn't list any cards for me to even try.  All it says is "NULL" like mythtv doesn't even recognize my sound card stuff.

Can anyone point me in the right direction here?  I'm so close, I just need sound.  Thanks!

---

### Post by NertSkull on 2011-07-30
Here is some output stuff that may help.

```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, VT2020 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, VT2020 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, VT2020 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, VT2020 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, VT2020 Digital
    Hardware device with all software conversions

```

I'm pretty sure I just need to figure out what to type in to the output area.  I tried

ALSA:iec958:CARD=SB,DEV=0

And it didn't work (I also tried just about every other combo on that list)

Also, I can't even start mythtv unless I first run "sudo killall pulseaudio" otherwise it tells me there is an error and that MythTV hasn't been compiled with Pulse Audio disabling support.  But I'm pretty sure thats unrelated error, and just because I didn't compile it right to automatically turn off pulse audio.

My SPDIF sound works fine outside of Myth.  I just don't know how to get MythTV to use it. 

What do I need to put into the output box for MythTV?

---

### Post by NertSkull on 2011-07-30
Allright, so for the enjoyment of others, this is what fixed it for me.

I went back and did ./configure again and looked at the output, and apparantly it was telling me that there was no ALSA support.  So I manually enabled it, and it told me there was an error and that my also needed to be a higher version.

Which was weird, because I already had a higher version installed than what it was asking for.

So, I did this

```
wget http://alsa.cybermirror.org/lib/alsa-lib-1.0.23.tar.bz2 
bzip2 -d alsa-lib-1.0.23.tar.bz2 
tar -xvf alsa-lib-1.0.23.tar 
cd alsa-lib-1.0.23 
./configure 
sudo make install 
```

Which didn't break my sound in general, which made me glad.

Then I went back to ./configure and now it said alsa was enabled

So I did make and then sudo make install again.  And all is well.

For my output device I set it to

ALSA:iec890:CARD=SB,DEV=0

And right now I just have it on Stereo - I'll cross 5.1 when I get the rest of my speakers built.

---

