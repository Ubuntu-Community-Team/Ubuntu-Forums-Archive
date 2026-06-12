---
title: "Sound problem"
date: 2011-01-20
forum: General Help
---

### Post by Svamp on 2011-01-20
Okey, so I just recently installed Ubuntu and have encountered problems with my sound.
The sound sounds like it's played in fast speeds and the same goes when I try playing a video file(also with streams like youtube). Anyone knows how to fix this problem?

I am also very new to Ubuntu and Linux so if you can keep it as simple as possible :)

Here is some stuff that might help:
[http://www.alsa-project.org/db/?f=387645f81648db87c04d54054a9aa0ee6a697fca](http://www.alsa-project.org/db/?f=387645f81648db87c04d54054a9aa0ee6a697fca)

From lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller

Let me know if there is any other information you need.

---

### Post by Svamp on 2011-01-20
bump

---

### Post by Vigh on 2011-01-20
what distro are you using? Maverick 10.10? ALSA/Sound should work fresh install with the latest distro, otherwise you may need to install build essentials through the terminal, and then compile ALSA from source, which is not that hard, just a bit difficult if your new to the system, I would just try for the latest distro, otherwise check ALSA-PROJECT site if your soundcard is compatible

you can find out what soundcard you have by typing i think in terminal

aplay -l

---

### Post by Sylos on 2011-01-20
I may well be completely wrong but it sounds like you could just be set to the wrong speed. I think the defualt should be 44k. Try looking in your sound preferences and see if there is an option to alter the frequency - if so alter it.

---

### Post by Svamp on 2011-01-21
> **Vigh said:**
> what distro are you using? Maverick 10.10? ALSA/Sound should work fresh install with the latest distro, otherwise you may need to install build essentials through the terminal, and then compile ALSA from source, which is not that hard, just a bit difficult if your new to the system, I would just try for the latest distro, otherwise check ALSA-PROJECT site if your soundcard is compatible

you can find out what soundcard you have by typing i think in terminal

aplay -l

I'm using Meverick 10.10 and my soundcard is compatible with the ALSA-PROJECT. I have not yet tried to install the build essentials. I have found how to do that so I'll try doing that.

> **Sylos said:**
> I may well be completely wrong but it sounds like  you could just be set to the wrong speed. I think the defualt should be  44k. Try looking in your sound preferences and see if there is an option  to alter the frequency - if so alter it.

I haven’t found where to do that yet, but I'll keep searching.

---

