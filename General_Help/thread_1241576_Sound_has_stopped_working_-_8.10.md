---
title: "Sound has stopped working - 8.10"
date: 2009-08-16
forum: General Help
---

### Post by Kerubu on 2009-08-16
Hello,

I've been using 8.10 for a while now with no problems with sound, however sound has stopped functioning correctly as of last night. I was using 'Digital Television for Gnome' and believe this has somehow corrupted the sound installation. (DVB did in fact crash when I exited it)

I've tried checking the card is recognised :

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

so that seems ok.

When I try checkin pulseaudio however :

```
 pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

I've tried re-installing the pulseaudio and alsa packages but to no avail.

Finally I should point out that when I do a test from Preferences->Sound, none of the ALSA or PulseAudio options work but the OSS ones do (audio tone is heard). 

** Leaving it set at AUTODETECT and trying to play a sound file or move results in a weak crackle from the speakers. This same crackling occurs on login to Ubuntu. **

Any help appreciated, but it seems Pulseaduio isn't playing ball.

---

### Post by marn on 2009-08-25
I have the same problem on 9.04. Playing sound only produces a weak crackle. I had a crash (actually a number recently) but nothing to do with sound/multimedia. The output I get from the card and pulseaudio is roughly the same. Setting the sound output to OSS also works.

I would also appreciate any help!

Thanks, Marn

Edit: Problem solved by turning up PCM in the volume control settings. Oops!

---

### Post by mess110 on 2009-08-25
I still have the same weak crackle when an event occurs on pidgin. so I just disabled pidgin sounds (like I always do)

but sound works for me.

---

