---
title: "e-uae amiga emulator capture sound pulseaudio"
date: 2009-12-10
forum: General Help
---

### Post by rumca.js on 2009-12-10
Hello

I'm just a beginner so I don't know really where to start....   I've installed through ubuntu software center (karmic koala) e uae amiga emulator. I want to capture a sound.
I found pulse audio tutorial somewhere on the net and I downloaded pulseaudio volume controle. If I open music in totem music player everything's fine. However if I open euae no audio stream is visible in pulseaudio.
I don't know much about alsa and pulseaudio, but I know that I am able to record sound from sound streams via audacity if I check in "configuration" of pulseaudio volume control Analog Stereo Output.

is there any "way" to capture a sound in e uae or in the system that it would record sound from soundcard properly.... ?

---

### Post by kostkon on 2009-12-10
What options are available in UAE's sound prefs?

---

### Post by rumca.js on 2009-12-11
well there's not much....

There's mode (None, no output, normal, accurate), channels (mono stereo mixed) and finally resolution (8bit 16bit).

---

### Post by rumca.js on 2009-12-12
I found a post in one forum leading to
[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html#pcm_plugins_file](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html#pcm_plugins_file)
is it possible to use this "plugin" or I have to install something? Could anyone help me with this thing because I don't know how to use it.

---

### Post by kostkon on 2009-12-12
OK. I can see that E-UAE is SDL-based. Thus, check if you have the following package installed in your system:
```
libsdl1.2debian-pulseaudio
```
if not, install it and check again if you can see E-UAE in the pulseaudio volume control.

If that doesn't work, then try the following. Open your *.profile* file, for example like this:
```
gedit ~/.profile
```
and add this line at the end:
```
export SDL_AUDIODRIVER=pulse
```
save, then logout and login again.

Hope that helps.

---

### Post by rumca.js on 2010-01-23
Hello again,
Unfortunately it does not work. 

I installed the package that you suggested, run emulator and....  I'm encountering few problems. Description of a problem:

- When I open pulseaudio volume control and then emulator throught console 
I see emulator error message: 
Can't open /dev/dsp: Device or resource busy

- When I open winuae and then pulseaudio volume control no sound bar is presented in volume control (device is also busy because e-uae captured it).

---

