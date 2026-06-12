---
title: "Getting working audio on an HP T5700 thin client"
date: 2010-07-10
forum: General Help
---

### Post by prupert on 2010-07-10
Hi

I have an old HP T5700 thin client. I have replaced the FLASH memory with an 2.5" hard drive and have installed a minimal version of Ubuntu Lucid on it.

I would like to get the audio to work - specifically the microphone.

sudo aplay -l gives:


```
**** List of PLAYBACK Hardware Devices ****
card 0: rev40 [VIA 82C686A/B rev40], device 0: VIA 82C686A/B rev40 [VIA 82C686A/B rev40]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

But there are no /dev/dsp devices or /dev/audio devices.

I have looked at both [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

but neither have helped.

Has anyone managed to get sound working on this box or has anyone got any suggestions for getting the microphone input to work?

---

### Post by monongahela on 2010-08-25
Hi Prupert, I'm trying to do the same thing with a T5700 and have had very little luck yet. I have tweaked around in alsamixer and managed some VERY faint recordings through my mic, but that is all.

Have you had any luck?

---

### Post by prupert on 2010-08-26
I sure did, I got audio recording working fine, I never tested playback though.

I wrote up about it here: 

[http://www.prupert.co.uk/2010/08/02/stream-live-audio-from-a-microphone-in-near-real-time-in-ubuntu/](http://www.prupert.co.uk/2010/08/02/stream-live-audio-from-a-microphone-in-near-real-time-in-ubuntu/)

I think I had to tweak the ASLA configurations, using the instructions here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
under the section titled "Is ALSA using the correct model?".

Once doing that, I was able to use ffmpeg to record audio and stream it over the network, using this command:

ffmpeg -v -1 -f oss -i /dev/dsp -acodec libmp3lame -ab 32k -ac 1 -re -f rtp rtp://234.5.5.5:1234

the key part being using -f oss and -ac 1 which stopped the awful echo it would produce if trying to record in stereo.

If you need further advice, I can power up the PC and dig out the necessary configuration files....

---

### Post by monongahela on 2010-09-09
Thanks Prupert! Sorry it took me so long to respond. I just saw your answer and now I'm really excited to give it a shot. I'll be in touch if I have any questions.

---

### Post by prupert on 2010-09-14
Best of luck....

---

### Post by monongahela on 2010-09-25
Prupert, what is the product number of your T5700. I have the DS435A#ABA and think that might be part of my problem.[COLOR=#000000][FONT=Arial Narrow]
[/FONT][/COLOR]

---

### Post by sindhughanti on 2011-11-30
Please help me here as well!
[http://ubuntuforums.org/showthread.php?p=11500566#post11500566](http://ubuntuforums.org/showthread.php?p=11500566#post11500566)

thanks!

---

