---
title: "A few questions before I go full linux"
date: 2010-08-25
forum: General Help
---

### Post by BeWop on 2010-08-25
Alright, so I was multibooting, and never use my windows partition so I figured I'd go full linux, but there are things I need to sort out before I do so, so here's a few questions:

1. I was told in order to fix sound problems with wine/crossover (and I use both), I needed to uninstall pulseaudio and install esound. This worked brilliantly, as everything still had sound, however I didn't have any sound volume control or use of my mic. How can I do something similar when I reboot, only have control over sound?

2. I read a few posts on how to increase boot time, and I found one where within the grub menu, you hit E and add "profile" or something like that. That worked well, and my boot time has been great, but I don't know how to do that if I'm full linux, because grub obviously doesn't show up. How do I do that?

---

### Post by Vakman on 2010-08-25
> **BeWop said:**
> Alright, so I was multibooting, and never use my windows partition so I figured I'd go full linux, but there are things I need to sort out before I do so, so here's a few questions:

1. I was told in order to fix sound problems with wine/crossover (and I use both), I needed to uninstall pulseaudio and install esound. This worked brilliantly, as everything still had sound, however I didn't have any sound volume control or use of my mic. How can I do something similar when I reboot, only have control over sound?

2. I read a few posts on how to increase boot time, and I found one where within the grub menu, you hit E and add "profile" or something like that. That worked well, and my boot time has been great, but I don't know how to do that if I'm full linux, because grub obviously doesn't show up. How do I do that?

ESounD? I thought this had died years ago or something, maybe I am wrong. You likely had to get rid of PulseAudio, but never have heard of having to do this.
Increase boot time? Why? And GRUB is still there, it justs boots into Ubuntu automatically, and I can't confirm if you will still have this option.

---

### Post by mendhak on 2010-08-25
For your second question, grub will still be there, with 'ubuntu' and 'ubuntu recovery' as menu options. 

Can't say much about pulseaudio with wine, but did you see [this](http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html)?

---

### Post by BeWop on 2010-08-25
> **Thisislaw said:**
> ESounD? I thought this had died years ago or something, maybe I am wrong. You likely had to get rid of PulseAudio, but never have heard of having to do this.
Increase boot time? Why? And GRUB is still there, it justs boots into Ubuntu automatically, and I can't confirm if you will still have this option.

Well, I don't know if sound worked with or without esound, as I uninstalled pulse and installed that in the same sitting.

Also, just because. I was wondering if it was possible.

---

### Post by BeWop on 2010-08-25
> **mendhak said:**
> For your second question, grub will still be there, with 'ubuntu' and 'ubuntu recovery' as menu options. 

Can't say much about pulseaudio with wine, but did you see [this](http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html)?

This is probably a double post, but this is awesome, thanks a bunch.

I need this to work with Crossover as well, however. Any options?

---

### Post by varunendra on 2010-08-25
For Grub menu, just press 'shift' while booting.

For your question about crossover, I think it should automatically pickup the same drivers & sound settings as wine does, because it is just an enhanced version of wine.

Have you already tried what mendhak suggested & are having no success with crossover?

---

### Post by BeWop on 2010-08-25
That did not work for crossover, however, it fixed wine perfectly.

---

### Post by techunit on 2010-08-25
I personally have never had any problems with wine except it errors after I install an application and launch it. Sound actually has worked quite well and I haven't need to do anything.

---

### Post by TNT1 on 2010-08-25
> **BeWop said:**
>  2. I read a few posts on how to increase boot time,   why would you want to?

---

### Post by BeWop on 2010-08-25
*decrease XD

Well, for crossover I could just temporarily disable pulseaudio, but I can't figure out how to do that without it randomly popping back up.

---

