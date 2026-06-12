---
title: "Only sound in left speaker?!"
date: 2009-07-04
forum: General Help
---

### Post by ericus on 2009-07-04
Hi, I have some troubles with my sound. It's not a hardware error.

Sound is only coming out of left speaker. I've tried everything that's described in these threads:

[http://ubuntuforums.org/showthread.php?t=917316](http://ubuntuforums.org/showthread.php?t=917316)
[http://ubuntuforums.org/showthread.php?t=917316](http://ubuntuforums.org/showthread.php?t=917316)
[http://ubuntuforums.org/showthread.php?t=167325](http://ubuntuforums.org/showthread.php?t=167325)
[http://forum.eeeuser.com/viewtopic.php?id=57081](http://forum.eeeuser.com/viewtopic.php?id=57081)

Nothing works. As said, not hardware error.

Help me!

---

### Post by ericus on 2009-07-05
Any ideas?

---

### Post by Nevart on 2009-07-05
This is not a solution as such, but something to try and then you can give us some feedback on what happens so we can try and help a bit.

Right-click on the speaker icon and select "Open volume control"

Then you will see a slider on the left called "Master" at the bottom there is an icon with a chain, so click the button to make it 'unlinked'.  This lets you move the sliders independently.

Move the left slider all the way down, and the right one all the way up.  You should not be getting sound only from the right side speaker.

Did that work?

---

### Post by ericus on 2009-07-05
I only have one bar for master. Tried unlinking PCM and all the others, didnt work either

---

### Post by Nevart on 2009-07-05
That is quite serious.  There should be two.  It may mean you have set it up as a mono system.  Or that your soundcard is reporting that it only supports mono output.

I will go an experiment a bit and see if I can reproduce that situation, but in the meantime post up anything you find out about the sound card that is installed. 

BTW are you running it in ALSA mode or OSS?

---

### Post by Nevart on 2009-07-05
Click on the preferences button in the volume control and uncheck "Master Mono" and check "Master".  Should have a two bar slider and probably stereo sound now.

---

### Post by DeMus on 2009-07-05
> **Nevart said:**
> That is quite serious.  There should be two.  It may mean you have set it up as a mono system.  Or that your soundcard is reporting that it only supports mono output.

I will go an experiment a bit and see if I can reproduce that situation, but in the meantime post up anything you find out about the sound card that is installed. 

BTW are you running it in ALSA mode or OSS?

Why 2? See my attachment.
I also have one master slider instead of 2 so I think this is pretty standard.

---

### Post by ericus on 2009-07-05
Alsa. Tried changing to OSS, but without result. Also, there's no master mono :(

---

### Post by moster on 2009-07-05
sorry, wrong..

---

### Post by ericus on 2009-07-07
Still the same problem.. I need help! ;)

---

### Post by ericus on 2009-07-08
Sorry for bump, but I dont want this thread to disappear. This problem is so f*cking annoying..

---

### Post by Soul-Sing on 2009-07-08
maybe this linkage is helpful: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

edit: ```
amixer info
```
and : ```
amixer
```
put the outcome here.

and: ```
lsusb
```

---

### Post by ericus on 2009-07-08
```
ericus@charlotte:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 4
  Simple ctrls  : 2
ericus@charlotte:~$ 

```

```
ericus@charlotte:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 65536 [100%] [off]
  Front Right: Capture 65536 [100%] [off]

```

```
ericus@charlotte:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 002 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
(not usb speakers)


Does those outputs look ok?

The strange thing is that sound has worked before on both speaker, and now it just doesnt.

---

### Post by ericus on 2009-07-10
It is now working, reinstalled some packages.
Hopefully it will stay this way :)

---

