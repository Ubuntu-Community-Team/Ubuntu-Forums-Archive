---
title: "ALSA on Desktop vs Server"
date: 2010-03-02
forum: General Help
---

### Post by jonmagic on 2010-03-02
I'm building a mini jukebox that uses Ubuntu 9.10 64bit Server, the music player daemon (mpd), and a custom server/gui I've built to go on top ([http://github.com/jonmagic/jukeman](http://github.com/jonmagic/jukeman)), and I'm having a hard time getting my production system to recognize the onboard sound.

My production system is an Intel d945gclf2d board, and audio out works fine if I install Ubuntu 9.10 64bit Desktop edition, but not if I go with the server version. Also, on my virtual machine where I developed this whole system, sound works perfectly fine using Ubuntu 9.10 64bit Server edition, so I know its possible to get sound working with the server edition.

When I run aplay -l on my production board (d945gclf2d) with server installed I get:

aplay: device_list:223: no soundcards found...

When I run aplay -l on my production board with the desktop edition installed I get:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Before I tried the desktop version (and found out sound worked there) I had tried just about every fix on every forum on the internet for the snd-hda-intel driver, including adding the model= and trying every model I could find for my chip (per [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)). But after installing the desktop version I looked at alsa-base.conf and it was identical to the one the server install setup.

At this point I'm starting to think I'm missing some sound package that desktop installs by default and server doesn't. In fact, after partially following these directions ([http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)) to remove gnome from the desktop install (removing hundreds of packages), sure enough, I lost my sound card, and aplay -l went back to listing no soundcards found...

Any idea what package is installed with the desktop version that server is missing? All I'm installing on server for testing is alsa-base (and its dependencies).

---

### Post by Ghost|BTFH on 2010-03-02
> **jonmagic said:**
> Any idea what package is installed with the desktop version that server is missing? All I'm installing on server for testing is alsa-base (and its dependencies).

Possibility:

linux-sound-base

You may also need a sound server, the desktop generally uses PulseAudio, but if you're going for pure ALSA, you may need Esound.

Not sure on either, but that would be my educated guess.

Cheers,
Ghost|BTFH

---

### Post by jonmagic on 2010-03-04
Installing a sound server didn't help, and installing alsa-utils installs the linux sound base by default. I've given up and am just going to use the desktop install and then remove gnome from startup.

---

