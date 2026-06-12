---
title: "how to keep oss sound format for all?"
date: 2009-12-24
forum: General Help
---

### Post by abhilashm86 on 2009-12-24
```
abhilash@abhilash:~$ aplay -l
aplay: device_list:223: no soundcards found...
abhilash@abhilash:~$ 

```

how do i get this working?? i downloaded oss format, now oss is playing, please help me getting back sound........

```
abhilash@abhilash:~$ osstest
Sound subsystem and version: OSS 4.2 (b 2002/200911060735) (0x00040100)
Platform: Linux/i686 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009

*** Scanning sound adapter #-1 ***
/dev/oss/oss_hdaudio0/pcm0 (audio engine 0): HD Audio play pcm1
- Performing audio playback test... 
  <left> 
OK <right> 
OK <stereo> OK <measured srate 47987.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/pcm1 (audio engine 1): HD Audio play pcm2
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47987.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/pcm2 (audio engine 2): HD Audio play pcm3
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47990.00 Hz (-0.02%)> 
/dev/oss/oss_hdaudio0/pcm3 (audio engine 3): HD Audio play pcm4
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47987.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/spdout0 (audio engine 4): HD Audio play spdifout1
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47987.00 Hz (-0.03%)> 
/dev/oss/oss_hdaudio0/pcmin0 (audio engine 5): HD Audio rec select1
- Skipping input only device
/dev/oss/oss_hdaudio0/pcmin1 (audio engine 6): HD Audio rec pcm4
- Skipping input only device

*** All tests completed OK ***
abhilash@abhilash:~$ 

```

---

### Post by chillicampari on 2009-12-24
> **abhilashm86 said:**
> 
how do i get this working?? i downloaded oss format, now oss is playing, please help me getting back sound........



If you're hearing the test music fine (it looks like you are?) the next step is to configure your applications to use it. This should help:  

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

*Most* stuff I found you can just change in the application preferences to use OSS (or you can find it in a config file, like MPD).

---

### Post by abhilashm86 on 2009-12-24
> **chillicampari said:**
> If you're hearing the test music fine (it looks like you are?) the next step is to configure your applications to use it. This should help:  

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)

*Most* stuff I found you can just change in the application preferences to use OSS (or you can find it in a config file, like MPD).

oh you just made my day!! now sound is working fine, thanks:)
pulseaudio kinda too bad n filthy?? just updated my kernel, all gone?? ALSA is best, easy to configure......
with both pulseaudio and alsa, i'm confused? what architecture?? who knows, lets hope best for next ubuntu release!!

---

### Post by chillicampari on 2009-12-24
Yay! I'm glad it's working! Yeah, Pulse was giving me problems and scratchy sound and even after trying everything in the setup guides it still wasn't right. And I never got Alsa working the way it used to so tried OSS4 and like it better. I think the idea is that Pulse is supposed to manage the audio for all applications over the top of Alsa to make it consistant and do some neat tricks, but it just doesn't seem there yet.  Yep, let's hope for the best!

---

