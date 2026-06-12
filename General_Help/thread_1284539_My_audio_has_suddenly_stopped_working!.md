---
title: "My audio has suddenly stopped working!"
date: 2009-10-06
forum: General Help
---

### Post by duckdown on 2009-10-06
Greetings all, novice user here, but I am having a problem suddenly..

I've been running Ubuntu on my HTPC for a while now, and without me knowingly doing any major changes, suddenly my audio output has stopped working!  I am not sure if I installed some kind of automatic update that broke something or what

I am using the digital coaxial out connection on my motherboard, by the way.

And, I know that it's a problem to my ubuntu-specific installation because it works fine in Windows, AND it's fine on my XBMCLive livecd, which is also an Ubuntu base


Here is the output 'aplay -L' on XBMCLive, with full WORKING audio..  All works fine, no problems at all, DTS passthrough is working great in XBMC and so on:

```

# aplay -L

default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```


And this is what 'aplay -L' shows on my regular installation, where the audio has suddenly broken..  I can't get any sound

```

# aplay -L

front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

slightly different as you can see -- the one with broken audio doesn't have a default device it looks like?  This is probably what is wrong?

Also, I ran 'alsamixer' on XBMCLive with the working audio and made sure the "broken audio installation" had the same maxed channels and nothing unmuted, just like XBMCLive, but still, no luck.

I am not very linux savvy yet but am trying to learn -- so I am not sure of what other appropriate info or command output I should have included

Any other needed info just tell me what commands to issue or whatever, I will gladly do it right away

Any help would be greatly appreciated ASAP because my HTPC is pretty much useless right now!  I have subscribed to the thread for instance notification

Thanks all!

---

### Post by ZaHACKieL on 2009-10-06
Are you able to try the sound in Windows or another OS?

ZL

---

### Post by duckdown on 2009-10-06
> **ZaHACKieL said:**
> Are you able to try the sound in Windows or another OS?

ZL

yes as i said, the sound works fine both in XBMCLive (Which is an Ubuntu variant) and in Windows both

It is only affecting my Ubuntu for some reason..like one of the package upgrades I installed screwed something up

How can I check if they are both using the same version of the same module or whatever?  I'm not sure how ALSA works :(

Can anyone please assist

thanks

---

