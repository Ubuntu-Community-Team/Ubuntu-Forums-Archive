---
title: "How to acces a mixer device?"
date: 2006-04-28
forum: General Help
---

### Post by TmP on 2006-04-28
Hi!

I'm trying to set up my tv using Tvtime. My wierd old motherboard didn't have a separate audio access, so I had to connect it to my CD audio port. So now I'm wondering how to redirect Tvtime volume control to cd. 

Actually there's tvtime-configure command:
>     This sets the mixer device and channel to use.  The format is device
    name:channel name.  Valid channels are:
      vol, bass, treble, synth, pcm, speaker, line, mic, cd, mix, pcm2,
      rec, igain, ogain, line1, line2, line3, dig1, dig2, dig3, phin,
      phout, video, radio, monitor
   

<option name="MixerDevice" value="/dev/mixer:line"/>
<

But guess what? I don't see /dev/mixer anywhere...
What should I address?

I'm guessing 
<option name="MixerDevice" value="/dev/SOMEDEVICE:cd"/>

Please help!

---

### Post by TmP on 2006-04-28
Damn... It looks grim.

here's my sndstat:
> Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux TmP 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
VIA 82C686A/B rev20 with AD1885 at 0xdc00, irq 11

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG


---

### Post by TmP on 2006-04-28
Can anybody explain this to me?

> 				VIA82xx mixer
				=============

On many VIA82xx boards, the 'Input Source Select' mixer control does not work.
Setting it to 'Input2' on such boards will cause recording to hang, or fail
with EIO (input/output error) via OSS emulation.  This control should be left
at 'Input1' for such cards.


It's a bit shady...
So how am I supposed to access this input1, and do I need to do that at all?

---

