---
title: "Suddenly - no sound on Acer 751 with Karmic"
date: 2009-11-25
forum: General Help
---

### Post by Udibuntu on 2009-11-25
Hi,

A couple of days ago I lost all sound on my Acer 751 running Karmic. 

I guess everything is there but I don't have access to it or something, since I do get the short drumming theme just before login, but that's it.

Alsamixer says all green, I tried a few things but nothing fixes the problem.

Is there a diagnostic and solution available?

---

### Post by BrockStrongo on 2009-11-25
> **Udibuntu said:**
> Hi,

A couple of days ago I lost all sound on my Acer 751 running Karmic. 

I guess everything is there but I don't have access to it or something, since I do get the short drumming theme just before login, but that's it.

Alsamixer says all green, I tried a few things but nothing fixes the problem.

Is there a diagnostic and solution available?

Not sure if this will help, but , when I first installed ubuntu 9.10 all the sounds were muted I had to unmute them in system->preferences--> sound. I also had to select the correct hardware profile.
Sorry if this is a waste of your time.

---

### Post by kio_http on 2009-11-25
Have you installed anything that would alter sound configuration like pulseaudio intentionally or even unknowingly that could occur by pulseaudio being a dependency for a KDE application

---

### Post by Udibuntu on 2009-11-25
> **BrockStrongo said:**
> Not sure if this will help, but , when I first installed ubuntu 9.10 all the sounds were muted I had to unmute them in system->preferences--> sound. I also had to select the correct hardware profile.
Sorry if this is a waste of your time.

It's not a waste of time my friend...

I tried to check and uncheck every option in my "sound" preference tab, no dice..

---

### Post by Udibuntu on 2009-11-25
> **kio_http said:**
> Have you installed anything that would alter sound configuration like pulseaudio intentionally or even unknowingly that could occur by pulseaudio being a dependency for a KDE application

Uhm, I don't know... is there a script to run and see if my sound stuff is in place?

UPDATE - Removed and reinstalled alsa files, got sound but system would mute after boot. set alsamixer right, then "alsactl store" as root, solved the issue.

---

