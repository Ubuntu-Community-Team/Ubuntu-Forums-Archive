---
title: "Pulseaudio in skype"
date: 2009-11-23
forum: General Help
---

### Post by RedSingularity on 2009-11-23
Is there a way to enable pulseaudio in the 2.0 version if skype?  Thanks.

---

### Post by mgol on 2009-11-23
No, it only works with 2.1 beta binary which is available in karmic medibuntu repo. You can get a deb here:
[http://www.skype.com/intl/pl/download/skype/linux/choose/](http://www.skype.com/intl/pl/download/skype/linux/choose/)
Choose one of Ubuntu versions (depending on You having a 32- or 64-bit Ubuntu).

BTW, I have Karmic and I uninstalled PulseAudio. It still gives me a headache...

---

### Post by Prodigal Son on 2009-11-23
> **mgol said:**
> 
BTW, I have Karmic and I uninstalled PulseAudio. It still gives me a headache...

It only gives you headache or something truly doesn't work ? :rolleyes: Even on minimal install ( which means, ALSA + Pulse *from scratch* ) everything works better than I expected.

---

### Post by mgol on 2009-11-23
Yeah, at the beginning it seemed OK to me. However, wine doesn't support PulseAudio and ALSA emulation in PulseAudio isn't perfect. I used to constantly loose sound in wine apps. I was sometimes loosing sound in Firefox, which is also run by this ALSA emulation. Generally, if an app uses PA directly, it seemed OK. But ALSA emulation isn't in its best shape...

To say the truth, I was using PA with Karmic for a month. But, finally, I gave up.

---

### Post by jocheem67 on 2009-11-23
Well, I'm on Arch nowadays and tried to install pulse through the arch-wiki. Gave me nothing but headaches and forced me in the end to do a fresh arch install..that's not how it's ment to be..:(

It showed me how difficult and integrated pulse ( still ) is in a further healthy linux-system.

---

### Post by mgol on 2009-11-23
To be honest - who really needs PulseAudio today? ALSA with its mixing abilities does well and I think maybe 1% of Ubuntu users would make use some fancy new features of PA. I think that Arch way not to recommend PA with default repositories is actually a good choice... At least in current stage of PA development.

---

### Post by Prodigal Son on 2009-11-23
> **mgol said:**
> To be honest - who really needs PulseAudio today? ALSA with its mixing abilities does well and I think maybe 1% of Ubuntu users would make use some fancy new features of PA. I think that Arch way not to recommend PA with default repositories is actually a good choice... At least in current stage of PA development.

As an example, Skype - by default it's way too loud and the only way to fix it is Pulse.

---

### Post by mgol on 2009-11-23
> **Prodigal Son said:**
> As an example, Skype - by default it's way too loud and the only way to fix it is Pulse.
I didn't notice that behaviour... For me it's OK.

---

### Post by Prodigal Son on 2009-11-23
> **mgol said:**
> I didn't notice that behaviour... For me it's OK.

I don't know, maybe it's just me. Skype is way louder than Audacious .. It's extremely annoying to listen to my music while hearing *whip whip* when the chat message arrives :D

---

### Post by RedSingularity on 2009-11-23
> **mgol said:**
> To be honest - who really needs PulseAudio today? ALSA with its mixing abilities does well and I think maybe 1% of Ubuntu users would make use some fancy new features of PA. I think that Arch way not to recommend PA with default repositories is actually a good choice... At least in current stage of PA development.


If you dont use pulseaudio though you can only listed to one piece of sound at a time correct?  The sound server allows you to listen to multiple audio streams.

---

### Post by mgol on 2009-11-23
> **RedSingularity said:**
> If you dont use pulseaudio though you can only listed to one piece of sound at a time correct?  The sound server allows you to listen to multiple audio streams.
That's not true. ALSA supports hardware mixing (though not for OSS emulation but OSS-only applications are rare - or I just didn't happen to see many of them). Sound from many applications works OK - and I didn't have to install esound package.

---

### Post by RedSingularity on 2009-11-23
Interesting.  So i can uninstall pulse and just use ALSA then?  Thats what i had before pulse but i could only play one audio stream at a time.

---

### Post by mgol on 2009-11-23
> **RedSingularity said:**
> Interesting.  So i can uninstall pulse and just use ALSA then?  Thats what i had before pulse but i could only play one audio stream at a time.
That was also true for me with Hardy which I used before Karmic. Now I just purged all PulseAudio packages:
```
sudo apt-get purge libcanberra-pulse pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev   pulseaudio-module-x11 gstreamer0.10-pulseaudio pulseaudio-utils pavucontrol 
```

Then I installed some ALSA-related packages (I'm not sure if they're necessary):
```
sudo apt-get install gnome-alsamixer alsa-oss python-alsaaudio 
```

After killing a pulse process everything works flawlessly (maybe a restart is needed but AFAIK it's not) - and mixing works (contrary to what I experienced in Hardy). Except two things - volume-related multimedia keys (volume up, volume down, mute) don't work and the speaker icon is gone from system tray. However, thanks to richie2.0 You can go there:
[http://ubuntuforums.org/showpost.php?p=8130297&postcount=25](http://ubuntuforums.org/showpost.php?p=8130297&postcount=25)
and follow the instructions. Now I have fully functional volume keys with nice notifications (similar to default once) and a speaker icon functional like the previous one. And problems are gone.

**EDIT:** default sound setting from System -> Preferences won't work after PA removal (thanks to GNOME folks for that one...), but gnome-alsamixer is a package that contains it's audio settings windows; it's available in Applications -> Sound & Video -> GNOME ALSA Mixer after installation.

---

### Post by RedSingularity on 2009-11-23
Well that works nicely!!  Guess i dont need this pulseaudio anymore!  Maybe its something in the newer versions of ALSA because i could never do this before.

---

### Post by mgol on 2009-11-24
To my previous post - apart from Wine and (a bit) Firefox there is another reason not to use PA - DOSBox. It was also giving me a headache, especially because of this bug:
[https://bugs.launchpad.net/bugs/429373](https://bugs.launchpad.net/bugs/429373)

PA feature to control sound volume in a per-application level is a nice idea... and maybe the only one in favor of PA (for a regular user). I don't understand why Ubuntu is constantly pushing PA to final releases. They should listen to Arch devs...

---

### Post by jocheem67 on 2009-11-24
There are several howto's on the web regarding the purging of pulse...it's not too hard and probably one will recognize the logic behind the good ones.

[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

This surely is a safe one. Still applies to the current ubuntu.

---

### Post by mgol on 2009-11-24
> **jocheem67 said:**
> 
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)

This surely is a safe one. Still applies to the current ubuntu.
But You don't need to install esound in Karmic. BTW, it does *NOT* apply to Karmic - for example because You can't run sound preferences without PA. Don't spread misinformation, please...

---

### Post by jocheem67 on 2009-11-24
You can, only pulse won' t be listed anymore. Tried it myself.

---

### Post by mgol on 2009-11-24
> **jocheem67 said:**
> You can, only pulse won' t be listed anymore. Tried it myself.
Ah, You're talking about releases previous to Karmic, don't You? Then maybe it's true; in Karmic it sure won't work.

---

