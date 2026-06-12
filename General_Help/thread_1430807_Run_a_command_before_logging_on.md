---
title: "Run a command before logging on"
date: 2010-03-15
forum: General Help
---

### Post by d3ngar on 2010-03-15
Hi there,

I was wondering if someone could help me figure out how I could run a command before logging on, in addition, the command needs to run as root.

This is going back to some few weeks months ago, shortly after I upgraded to Karmic Koala. Since then, the sound device doesn't work automatically. I donno why, but alsa doesn't seem to detect the audio device.

Once I have booted the machine, I can access sound by doing:
```
sudo alsa force-reload
```
Needless to say, that's pretty annoying and I posted two or three threads to find a solution to this problem, but never got anywhere.

Failing that I get the issue resolved, I was wondering if someone could maybe give me some advise about running the 'alsa force-reload' command at boot up, so that when I'm logged in, it's already working.

Any help much appreciated...

---

### Post by Mr Nemo on 2010-03-15
You could write a simple script and then set it as a startup application.

```

sleep 10 && sudo alsa force-reload

```

---

### Post by d3ngar on 2011-01-07
This kind of sorted itself over time.

---

