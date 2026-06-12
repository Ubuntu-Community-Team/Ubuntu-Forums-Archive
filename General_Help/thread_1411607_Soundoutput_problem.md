---
title: "Sound/output problem"
date: 2010-02-20
forum: General Help
---

### Post by ccbn on 2010-02-20
Hi i'm kinda new to this, ubuntu community, that's why i need your help to fix this problem i like it very much so far the only problem is that i got no sound. Maybe it is me who is stupid but i have many kinds of outputs and i don't know which one to use.

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

One more question how do i test my sound? The only way i can find out is to use youtube/flash to see if the sound works.

---

### Post by bobcollard on 2010-02-20
> **ccbn said:**
> Hi i'm kinda new to this, ubuntu community, that's why i need your help to fix this problem i like it very much so far the only problem is that i got no sound. Maybe it is me who is stupid but i have many kinds of outputs and i don't know which one to use.

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

One more question how do i test my sound? The only way i can find out is to use you tube/flash to see if the sound works.
Click on the speaker or control knob in your taskbar.  Configure your sound there, you may find it is muted at every startup or reboot.  If you have a CD you like to listen to, slip that into your computer.

---

### Post by ccbn on 2010-02-20
Thanks for the fast reply but i have already tried to configure it through system - settings - sound. It seems i have tried every possibility. I tried all outputs even if it was input. There's no muting on the output and programs. It looks like that ubuntu doesn't recognize my internal audio. Here is the outputs i have tried:
analog stereo input
analog stereo output
analog stereo duplex
digital stereo duplex
digital stereo (IEC958 ) Output + analog stereo inpu

---

### Post by bobcollard on 2010-02-20
> **ccbn said:**
> Thanks for the fast reply but i have already tried to configure it through system - settings - sound. It seems i have tried every possibility. I tried all outputs even if it was input. There's no muting on the output and programs. It looks like that ubuntu doesn't recognize my internal audio. Here is the outputs i have tried:
analog stereo input
analog stereo output
analog stereo duplex
digital stereo duplex
digital stereo (IEC958 ) Output + analog stereo inpu
Does your panel under the sound icon look anything like this?

---

### Post by ccbn on 2010-02-20
It looks like this. It isn't exactly the same.

---

### Post by bobcollard on 2010-02-20
> **ccbn said:**
> It looks like this. It isn't exactly the same.
Wrong panel.  Okay, lets start over.  I don't know if your task bar is on top or bottom of your screen.  It does not matter, a personal choice.  In the right side with your Internet icon there is another icon for sound.  Left click on that and if it does not look like mine, or similar, you need to set it up.  On the bottom left of that panel is a box marked "Select Controls"  Choose at least Master and speakers.  This will give you something to work with.

---

### Post by ccbn on 2010-02-20
When i right-click the sound icon it doesn't show more than "mute" and "sound settings". Sound settings was that window i showed you

---

### Post by bobcollard on 2010-02-20
> **ccbn said:**
> When i right-click the sound icon it doesn't show more than "mute" and "sound settings". Sound settings was that window i showed you
I know, that's why I said left click it.

---

### Post by ccbn on 2010-02-20
> **bobcollard said:**
> I know, that's why I said left click it.

Oups, sorry. But still left clicking just shows volume bar and no select controls at the bottom or have i misunderstood something again?

---

### Post by stoneage on 2010-02-20
Try selecting Analog Stereo Duplex. It was the default for me and it works......but use your soundcard, not the onboard sound.

Mine looks like this:-
[ATTACH]147654[/ATTACH]

---

### Post by ccbn on 2010-02-20
> **stoneage said:**
> Try selecting Analog Stereo Duplex. It was the default for me and it works......but use your soundcard, not the onboard sound.

Mine looks like this:-
[ATTACH]147654[/ATTACH]

thanks
I tried to use the same settings as you but mine is still not working. 

Mine is looking like this now. It isn't the same as yours because i cant choose "audio stereo duplex", where mine says "R700 audio Devic...". Only the one above

---

### Post by ccbn on 2010-02-20
Ok i have found it works using "Audio stereo duplex" with headset but is very low and is not on low volume either is the one on the headset. But i also want the sound on my laptop to work. Any ideas?

1. Audio Stereo duplex works with headset, but is very low..
2. Laptop sound still doesn't work.

---

### Post by bobcollard on 2010-02-20
Raise the volume above 100%

---

### Post by ccbn on 2010-02-20
it is above 100%

---

### Post by JosephMarc on 2010-02-20
open terminal and type "alsamixer" , you should be able to change your sound settings from there, after that press escape to save and exit.

---

### Post by stoneage on 2010-02-20
I would guess your system is still using the onboard sound then, rather than the soundcard. I think you will have to resolve that first. There are many threads on sound, try searching the forum. Some very good troubleshooting threads have been started by markbuntu, try searching for those. Here is one of them:-
[http://ubuntuforums.org/showthread.php?t=922860&highlight=markbuntu+sound](http://ubuntuforums.org/showthread.php?t=922860&highlight=markbuntu+sound)

---

