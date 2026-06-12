---
title: "Trying to install ALSA, error on make install (no sound)"
date: 2010-07-25
forum: General Help
---

### Post by greenchance on 2010-07-25
Ok, I have NO sound on my computer since upgrading to 10.04. I find the alsa instuctions for my card/chipset, download alsa, and settle in for a long install process. 

So, after navigating through what may be the worst instructions of my life, I finally get to the last step of installing. I do ./configure. Works fine. I type make, also fine. I type make install, and get this:

```
rm -f /lib/modules/0.0.0/misc/snd*.*o /lib/modules/0.0.0/misc/persist.o /lib/modules/0.0.0/misc/isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
mkdir -p /lib/modules/0.0.0/misc
cp snd-hpet.o snd-hwdep.o snd-page-alloc.o snd-pcm.o snd-rawmidi.o snd-timer.o snd.o /lib/modules/0.0.0/misc
cp: cannot stat `snd-hpet.o': No such file or directory
cp: cannot stat `snd-hwdep.o': No such file or directory
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-rawmidi.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory
make[1]: *** [_modinst__] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [install-modules] Error 1

```

Could someone please tell me what I did wrong? I can't believe I made it through those crap instructions only to get hung up on the last step. *bang head*

---

