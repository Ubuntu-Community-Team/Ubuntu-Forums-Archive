---
title: "Forcing monophonic audio output"
date: 2010-07-24
forum: General Help
---

### Post by Mojo McCracken on 2010-07-24
My audio setup is based on a single guitar amplifier, and from this I suffer from only being able to listen to one of the two stereo channels. Since I honestly don't care for stereo, I'd rather force Ubuntu to output **all** audio as mono instead of "upgrading" to a stereo compatible setup.

Is there a way to do this?

Thanks in advance.

---

### Post by lidex on 2010-07-24
If the sources are all stereo I don't know how you could combine the two channels to get one monophonic. I would suspect some signal cancellation/ degradation would occur.

---

### Post by Mojo McCracken on 2010-08-02
Bump.

---

### Post by coldraven on 2010-08-02
What is the input impedance of your amp?

---

### Post by coldraven on 2010-08-02
Okay, let's assume your amp has a 1K (1000 Ohms) input impedance the you could make the simple circuit that I've attached.
It would most likely be High impedance (10K or 10000 Ohms) or Low impedance (maybe 600 Ohms).
You might have a choice of Mic. or Guitar inputs. RTFM ;)
The Low one may work better.
Do not stand in a bucket of water whist connecting up this circuit especially if you have a tube amp :p

---

### Post by Mojo McCracken on 2010-08-03
First of all, thank you for the attention.

Apparently, the impedance claims to be a mere 8.

I don't know if this has any significance, but the amp is directly connected via a 3.5mm jack (computer output) to a 3.5mm jack with a 3.5mm/6.35mm jack adaptor in the amplifier's input.

---

### Post by coldraven on 2010-08-03
The 8 refers to the output impedance to match to your  8 Ohm speaker.
Ask a local friend who plays an electric guitar for advice.
Good luck.

---

### Post by Mojo McCracken on 2010-09-15
Bump. I've been continuously trying to make this work, and nothing does.

---

### Post by Mojo McCracken on 2010-11-17
Bumping again. This is really getting to me...

Lately I've tried using [Audacious]("http://audacious-media-player.org/") with the [aud-mono-plugin]("http://ahans.de/aud-mono-plugin/"), only to be greeted by this frustrating babble:

```
Package audacious was not found in the pkg-config search path.
Perhaps you should add the directory containing `audacious.pc'
to the PKG_CONFIG_PATH environment variable
No package 'audacious' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
cc  -s -Wall -fPIC -ffast-math -fomit-frame-pointer   -c mono.c
mono.c:24: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
make: *** [mono.o] Error 1
```

Can somebody at least help me with the above?

---

