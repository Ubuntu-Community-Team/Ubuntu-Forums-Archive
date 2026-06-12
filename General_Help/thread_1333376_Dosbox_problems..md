---
title: "Dosbox problems."
date: 2009-11-21
forum: General Help
---

### Post by GroogFish on 2009-11-21
I'm trying to play the original xcom on dosbox but it's buggy.

1. The screen is flattened a bit.
2. Their are random blips and bleeps that aren't supposed to be there.
3. Sound affects are nearly a second late.
4. Sometimes the cursor or units leave a graphic trail of themselves.

Is it a problem with linux, the settings, or maybe dosbox?

---

### Post by rCXer on 2009-11-21
This might be a [known bug](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/429373) that often occurs in karmic. Someone had the [same problem and fixed it](http://ubuntuforums.org/showthread.php?t=1300669) by changing the sound mixer's rate in their configuration file. To do this if you haven't already...

* Run dosbox
* Type "config -writeconf dosbox.conf" into the prompt. This should create a "/home/username/dosbox.conf" file
* Open it and scroll down to the line that says...
```

rate=22050

```
and change it to...
```

rate=44100

```

You could also try switching to libsdl-esd from pulseaudio as someone else suggested in the bug report...
```

sudo apt-get install libsdl1.2debian-esd
sudo apt-get remove pulseaudio

```
... but this is much more risky ;)

---

