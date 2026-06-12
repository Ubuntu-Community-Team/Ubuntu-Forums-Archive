---
title: "Sound problems VIA AC97"
date: 2006-02-10
forum: General Help
---

### Post by malaria on 2006-02-10
I have been having distorted sound ever since installing Ubuntu (both Breezy and Hoary). I have on board sound card VIA AC97 but all sound is distorted. The louder sounds have a very trebly crackle all over them.

I have tried a number of things including changing the Default Sink in "Multimedia  System Selector" and setting the PCM volume at <50% and muting all else.

I dont really know what else I can do. Sound works fine in windows and other linux distros. Please any suggestions.... I dont know how to uninstall and re-install sound drivers which is what I want to try next.
thanx

---

### Post by Paloseco on 2006-02-10
Most of the times this happens because volume is set to 100%, the PCM, the Master and the others, and above 90% you always experiment distortion. I have an AC97 too and works perfec, so try to launch all programs that control sound like amix, kmix, etc and turn down the volume.

---

### Post by malaria on 2006-02-10
tried doing this and have even turned everything down as low as it will go but still no luck. Is there any other things I can try?

---

### Post by annsachd on 2006-02-10
Likewise, I have AC97 and it works fine.

---

### Post by Paloseco on 2006-02-13
You can try the latest dapper drake development release, some audio problems are solved :) .

---

### Post by NatvAmer on 2006-02-27
[QUOTE=malaria]I have been having distorted sound ever since installing Ubuntu (both Breezy and Hoary). I have on board sound card VIA AC97 but all sound is distorted. The louder sounds have a very trebly crackle all over them.

I have tried a number of things including changing the Default Sink in "Multimedia  System Selector" and setting the PCM volume at <50% and muting all else.

I dont really know what else I can do. Sound works fine in windows and other linux distros. Please any suggestions.... I dont know how to uninstall and re-install sound drivers which is what I want to try next.
thanx[/QUOTE]
I was having the exact same problem and I have been able to correct it just tonight by following the instruction in the Unofficial Ubuntu 5.04 Starter Guide.

[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

I still am not able to use the master volume control, yet. But I am sure someone here will be able to help me.

---

### Post by mcmv200i on 2007-02-16
> **malaria said:**
> I have been having distorted sound ever since installing Ubuntu (both Breezy and Hoary). I have on board sound card VIA AC97 but all sound is distorted. The louder sounds have a very trebly crackle all over them.

I have tried a number of things including changing the Default Sink in "Multimedia  System Selector" and setting the PCM volume at <50% and muting all else.

I dont really know what else I can do. Sound works fine in windows and other linux distros. Please any suggestions.... I dont know how to uninstall and re-install sound drivers which is what I want to try next.
thanx

I had the same problem with the distortion with my Onborad VC97 alias VIA 8235 or whatever it is called. In my case putting the sampling rate from 44.1kHz up to 48kHz solved the problem.  
 
 I did that with KDE: systemsettings => Sound => Hardware => Custom Sampling rate = 48000 Hz. There must be some way to archieve this with ALSA directly or with other desktops envs, too, but thats your turn to find out how, sorry. :) Also have a look here: [http://alsa.opensrc.org/Via8233](http://alsa.opensrc.org/Via8233)

---

### Post by bishman on 2007-02-18
Malaria,
I see your post was a while ago, but did you ever get it working properly? I'm having the same problem with AC'97 in edgy... any help would be great

---

