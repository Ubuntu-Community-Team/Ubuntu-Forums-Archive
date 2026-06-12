---
title: "I broke compositing (video problem)."
date: 2010-12-15
forum: General Help
---

### Post by ninjaaron on 2010-12-15
I just did a fresh install of Ubuntu on my old macbook (which was playing possum for a year), and everything was great, except the sound and the iSight, but those are known bugs with fixes, so we're ok.

Anyway, I was playing some video, and there was a problem of some kind. The video played, but it looked like **** and said something about my driver.

I tried to dl the old nvidia driver, which I apparently did. Anyway, on reboot, none of my desktop effects were on. I went to appearances, and the effects were set to "none," so I tried to change it to "normal." It wouldn't let me. It said I didn't have the drivers for that stuff.

I uninstalled the nvidia stuff, thinking that could be the problem. Reboot. same thing.

It could be unrelated to the nvidia thing, of course, but I'm not sure what else I've done that could have effected the video.

So now what?

---

### Post by ninjaaron on 2010-12-15
Ok, I went into synaptic and did a reinstall on everything related to open GL or nvidia.

Didn't help.

[edit]
also tried installing all the old nvidia drivers.

didn't work either. my old macbook gen 2.1 sound bug did come back after this.

[edit]
reinstalling the kernel didn't seem to work either.

[edit]
also noticed that I can't force the grub menu at boot any more after reinstalling the kernel... weird.

So am I just completely destroying my computer or what?

[edit]
tried fixing broken packages in synaptic. There don't seem to be any.

[edit]
so I tried reinstalling compiz, and I went to the terminal and typed 

compiz --replace

and I got these messages:
```
Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

I'm gonna see about this Xlib GLX thing... hmm...

---

### Post by ninjaaron on 2010-12-15
well, I got the sound to work right again. Still no boot menu.

Anyway, if nobody knows how to fix my video problem, I'm going to reinstall the whole system when I get home.

How could anyone use a work environment without open GL?
;)

---

### Post by ninjaaron on 2010-12-15
Ubuntu reinstalled.

"solved"

:p

---

