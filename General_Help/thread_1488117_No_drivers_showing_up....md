---
title: "No drivers showing up..."
date: 2010-05-19
forum: General Help
---

### Post by mclizardman24 on 2010-05-19
Why are there no drivers showing up under hardware drivers? i don't have anything installed, and everything is running really glitchy. All things are up to date. (besides drivers)

---

### Post by davidmohammed on 2010-05-19
hardware drivers are only displayed if there are any third-party drivers particular to your system.  Thus if there are none displayed, then you have all the drivers you need anyway.

Can you expand "glitchy" - what are the issues and when does it occur and are there any patterns to reproduce the problems?

---

### Post by mclizardman24 on 2010-05-19
Well, it says no drivers are in use. And by glichy i  mean any games like the ones on armorgames.com don't work right, the sounds completely lagging with the actions. I have flash installed from the ubuntu software center.

---

### Post by linuxman94 on 2010-05-19
It is ok that no drivers are in use, that just means that the hardware on your system doesn't need proprietary drivers.

As for the slow flash, see this webpage.

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html]("http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html")

---

### Post by davidmohammed on 2010-05-19
what version of ubuntu are you running.

dump the contents of lspci here.

Are you using metacity or compiz?

Are you using pulseaudio or alsa for your audio.

Are your issues only Flash related or running graphic/audio/multimedia in general.

If Flash, what resolution are you running 360p or higher - possibly you are running at a higher resolution that your graphics card can cope with.

---

