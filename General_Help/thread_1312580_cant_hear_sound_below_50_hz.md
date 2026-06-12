---
title: "cant hear sound below 50 hz"
date: 2009-11-03
forum: General Help
---

### Post by nerdy_kid on 2009-11-03
Hey all, i just bought a pair of headphones with a frequency response of ~30hz-~2000hz but i cant hear frequency below 50hz!  I tested using    speaker-test -t sine -f hz   and 50 was as low as i got.  I remeber reading somewhere that ALSA or pulse use low frequency protection, but i cant find where i read it.  Any ideas?  thanks in advance...

---

### Post by Giblet5 on 2009-11-03
Some people just *can't* hear notes below 50Hz and they don't find that out until they use headphones. Anyone can *feel* a 32Hz note, but very few can actually hear it.

Men can typically hear higher notes; women, lower.

You may have damaged your eardrums with sustained loud sounds or by swimming. It won't hurt to get your hearing tested every few years. You can even get a cool response curve chart to shake at the geeks at the high-end audio stores.

Your headphone's specs seem wrong: is that higher frequency supposed to be 20,000Hz? The 30Hz lower range is also suspect as headphones don't really have the limitations that sealed-enclosure or bass-reflex speaker systems have.

Borrow someone else's headphones - preferably Sennheiser or Grado - and run this test again.

I have a pair of Sennheiser 590s. I can't hear notes below 38Hz but I can feel my ears flapping all the way down to 10Hz where an Audigy2 sound card just can't produce a sine wave with only 24 bits. :)

To my knowledge there is no sound card that uses a hardware "Rumble Filter" and the Linux audio system certainly doesn't use one by default. Rumble filters usually kick in at 20Hz anyway.

---

### Post by P4man on 2009-11-03
the original poster is correct. alsa or pulse seems to cut the sound below 50Hz. I ran his test and I can hear my bassbox at 51 hz but total silence at 50 Hz (and it shuts off so its not getting a signal. My bassbox automatically goes in sleep mode when not getting a signal, so its not my ears)

That said, whatever you'd hear at 50Hz or below is probably more noise and crossover than 50 Hz so i wouldnt worry too much about it.

FWIW Im using an audigy 1. Im not sure if that could be the limiting factor

---

### Post by Giblet5 on 2009-11-03
The speaker-test program is broken. So sayeth my oscilliscope.

Specifying anything below 50Hz produces a 50Hz tone.

(All are 48Khz sample rate, 16-bit, Creative Audigy2 configured for 5.1 analog, tested with Fluke scope, front-left output)

sound-test -t sine -f 120: 122Hz
sound-test -t sine -f 60: 60.6Hz
sound-test -t sine -f 50: 50.2Hz
sound-test -t sine -f 45: 50.2Hz
sound-test -t sine -f 41: 50.2Hz
sound-test -t sine -f 40: 50.2Hz

```
$ speaker-test -t sine -f [COLOR="DarkRed"]40[/COLOR]

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
[COLOR="DarkRed"]Sine wave rate is 50.0000Hz[/COLOR]
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
```

---

### Post by nerdy_kid on 2009-11-03
as to the specs, yeah sorry i lost the box so i couldnt remember the high end; 20000 is probaly right.  However, the audio is still cut off at 50hz, (as P4man comfirmed).

I dont blast music a lot, so my hearing is most likley fine; thanks for the tip ;)

---

### Post by P4man on 2009-11-03
you're right. And I must have mistyped or something because now indeed I do hear the same 50Hz hum even if I set lower values.
:confused:

---

### Post by Giblet5 on 2009-11-03
Watch the opening to "Transformers 2" and listen with headphones.

There are solid 28Hz notes in the opening credits that those headphones will reproduce and that you will at least sense, if not hear.

There is a launchpad bug report against speaker-test [(321477)]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1264488.html").

---

### Post by nerdy_kid on 2009-11-03
hmmm i suppose the bug with speaker-test would explain things lol
yeah, ill go fish for some media to play...thanks a bunch for your help!

---

