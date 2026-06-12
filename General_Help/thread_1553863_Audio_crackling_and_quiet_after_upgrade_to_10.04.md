---
title: "Audio crackling and quiet after upgrade to 10.04"
date: 2010-08-15
forum: General Help
---

### Post by sparkmandrill on 2010-08-15
Hello, I upgraded to Lucid and so far I managed to solve all the errors that occured myself, but this particular thing just won't work.

What happened: 
After the upgrade, the audio was very quiet and the little sound that came from my speakers was crackling. I fiddled around with the volume controls and managed to actually hear something. I started a youtube video and after about 3 minutes into the video my sound suddenly changed into a loud static sound.

What I did in attempt to fix this:
1. Reboot. Didn't help. Sound remained just static.
2. Followed these steps [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies) The audio now crackles even more than at the beginning and is even quieter than right after the upgrade.
3. Tried to use alsamixer in terminal. I'm getting "cannot open mixer: No such file or directory". Appearently alsamixer is part of alsa-utils? I also tried to install alsamixergui from synaptic, but it seems the tool doesn't recognize my audiocard.

I booted up Windows to make sure this wasn't a hardware defect as well.

Any help here would be appreaciated since I use this box mainly to listen to webradio and to watch videos. Thanks in advance!

---

### Post by Karl1982 on 2010-08-15
Is it actually using alsa?  I wonder if maybe you got switched to pulseaudio or something.

Also, Mega Man is awesome.

---

### Post by sparkmandrill on 2010-08-15
I thought pulseaudio was my soundserver while alsa was my  hardwaredriver, but if it's a pulseaudio problem, how would I go about  configuring that? So far the System>Preferences>Sound tool was of  no help at all. If I remember correctly, there used to be a much more  powerful tool in this spot. Is that still accessible?

I just tried purging and reinstalling pulseaudio with no results.
I'm running out of ideas.

And yes, Mega Man is pretty awesome.

---

### Post by simosx on 2010-08-16
Alsa is the Linux kernel subsystem for sound in Linux. It's low-level and offers basic sound support. Some applications use Alsa directly, however for a desktop system it makes sense to use PulseAudio, which is an audio server. It can do amazing things like recording from the soundcard (in an easy way) and supports network sound (forward your mic to another computer).

So, if you have sound issues, you need to be able to figure out whether it's really PulseAudio or it's Alsa to start with.

A user had an issue with sound and it was related to the graphics card; apparently the 3D support (compiz) was taking up too much processing power so that PulseAudio was not able to work properly. If you use the proprietary NVidia drivers, you may be affected.

If you want to figure out if it's the sound card at fault, google for 'alsa-info.sh' and provide your link to the alsa-info hardware details.

---

### Post by sparkmandrill on 2010-08-17
Okay, now I tried to install the backport packages I found in synaptic.  After installing I rebooted and all the Kernel  versions in grub gave me  a black screen on boot. After that I tried to boot the first one in  recovery mode and chose "repair broken packages" and it updated some  stuff. Then I resumed normal boot. The sound was still quiet and  crackling, so I wanted to try fiddling around with it a little more.

To my surprise the GNOME Alsa Mixer I installed earlier displayed a USB  soundcard (my soundcard is onboard though) instead of nothing. There I  could adjust the Volume just fine and the audio quality was back to  normal. Joy!

After rebooting again though I recieved a series of black screens from  all the Kernel versions in grub again. So I tried the recovery mode  thing again. Upon "resume to normal boot" this time it would just  present me a command line. I tried to start gdm but the terminal told me  there was no display specified. I restarted and tried to boot that  Kernel version again without recovery mode and it actually booted fine.

The audio is back to its quiet crackling again. I hoped that GNOME Alsa  Mixer would fix this again, but it was back to displaying nothing. When I  click Edit > Sound Card Properties it crashes giving me the  following error in terminal:

(gnome-alsamixer:1816): GLib-GObject-CRITICAL **:  g_type_instance_get_private: assertion `instance != NULL &&  instance->g_class != NULL' failed
Segmentation fault

It took me forever to get everything running how I wanted it to before  the update to lucid, so I really don't want to do a clean install right  now.

So... any ideas?

---

