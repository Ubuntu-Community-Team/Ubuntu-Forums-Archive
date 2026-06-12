---
title: "Sound ony plays through headphones"
date: 2010-11-13
forum: General Help
---

### Post by llawwehttam on 2010-11-13
Yesterday I was listening to music through my headphones and suspended my laptop with them plugged in, unplugged them and put them away.

Turned it back on today and the laptop obviously thinks that they are still plugged in as it won't play any sound through the internal speakers but sound comes out of the headphones when I plug them in.

I have tried a few reboots with combinations of having the speakers plugged in and unplugged and I have tried forcing alsa to reload all modules with no sucess.

And before anyone says it, yes, the sound is not muted.

some info that may be of help:

```
$ uname -r
2.6.31-22-generic

```

Running Ubuntu 9.10 x86_64

```
$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

```and my /etc/modprobe.d/options file reads:

```
options snd-hda-intel power_save=0

```to stop popping sounds, which has worked fine for a while now.


any ideas or help much appreciated.

---

### Post by llawwehttam on 2010-11-13
Mnaged to fix it.

Plugged the headphones in, shutdown, turned on again (with the headphones still in),
logged in, turned music on, unplugged headphones.

All is good.

Pity that there is that small irritating bug there. Guess it doesn't matter anyway as 9.10 is over in April.

Not sure yet whether to continue using ubuntu or switch to arch like my desktop.

EDIT: Using archlinux now, the date is 01/04/2012 (not april fools, don't worry.)

I ran into the same problem and found my own thread without a workable solution.

If you read this again and have the same problem, you ran:

```
sudo rmmod -f snd_hda_intel
sudo modprobe snd_hda_intel model=MODELNAME
```

for every model in the list here: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt)

Turned out that even with the clevo laptop the 6stack-dell model worked the best. Power saving is still meh as it caused crackling but I'll have to live with it.

---

