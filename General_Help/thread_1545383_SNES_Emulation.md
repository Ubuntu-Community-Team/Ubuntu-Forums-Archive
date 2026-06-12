---
title: "SNES Emulation"
date: 2010-08-03
forum: General Help
---

### Post by snowmanman on 2010-08-03
I'm trying to use a SNES Emulator with Ubuntu but there seem to be some problems.

With ZSNES, the sound is very choppy. I was fiddling with ALSA awhile back and this was the only program effected. I don't know of this is fixable since I have no idea what I did.

With Snes9x, I can't go fullscreen without extreme slowdown. I know my computer can handle it though. I used Snes9x all the time on XP on the same computer.

Could someone help me fix one of these problems? Once I get one working I should be fine.

EDIT: I ran "sudo zsnes" and got this:

```
matt@matt-desktop:~$ sudo zsnes
[sudo] password for matt: 
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: Logitech USB Receiver
Mouse 1: Macintosh mouse button emulation

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

Device 0 RetroUSB.com RetroPad
  2 axis, 8 buttons, 0 hats, 0 balls
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.
ALSA: underrun, at least 0ms.

```

It ran, but the sound was still choppy.

---

### Post by Yuri sss on 2010-08-03
Which version of Ubuntu and zsnes are you using?

This repository has the most recent version of zsnes (built eight weeks ago) in 32-bit and 64-bit:
[https://launchpad.net/~smaxein/+archive/ppa](https://launchpad.net/~smaxein/+archive/ppa)

You could also try changing the sound to PulseAudio.

---

### Post by snowmanman on 2010-08-03
I'm using 10.04 Lucid and whatever version of ZSNES is in the Ubuntu Software Center. Not sure how to download the build in the link you gave me. Once again, I was messing with ALSA and that probably screwed it up.

---

### Post by 1serveyou on 2010-08-11
> **snowmanman said:**
> I'm using 10.04 Lucid and whatever version of ZSNES is in the Ubuntu Software Center. Not sure how to download the build in the link you gave me. Once again, I was messing with ALSA and that probably screwed it up.

If you go to your application center, "edit", "software sources" , "other software", and then type in the address he has on his site. After that search for zsnes in the application center and it will be there :)

---

### Post by KresentPhresh on 2010-11-16
Just a random note, I was having weird slowdown issues with Snes9x as well. I found the problem having something to do with the emulator trying to keep the video and the audio synchronized, so oddly enough, the fix was to change the Sound Driver from PortAudio to ALSA (or whatever your preference.) Now works like a charm.

---

