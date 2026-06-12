---
title: "Jaunty + Audio is getting frustrating."
date: 2009-08-20
forum: General Help
---

### Post by Cygoku on 2009-08-20
The past week, I had multiple problem with audio un Jaunty.   daysago I formatted again ans installed Jaunty on

AMD Barton 3000+
Hercule Muse LT (SoundCard)

Since this time I had no problem at all with the audio.  When I got back from work this evening, there was a very small update from libgnutls and yesterday something about kernel updates,...  

Video and music were still #1.  I've restarted the computer and the freaking audio IS GONE AGAIN !! 

How can this happened again ?? How can Jaunty be so cruel and shitty about sound.  Let's hope the Christ that pulseaudio isn't the problem again or Canonical will ear from me hard.  

How can I try to diagnose the problem this time.  I followed many tutorial to remove pulseaudio and such without success (not on the actual config).  Only regular updates were done.  

Cygoku

---

### Post by Cygoku on 2009-08-20
What can I do to know what's locking the sound card ?? 

Cygoku

---

### Post by janascii on 2009-08-20
The same has happened to me after the update on my mythbuntu install. 

I have it setup with a digital coax cable only and the analog would mix to pcm and be sent to my receiver... now only the passthrough audio is working.

---

### Post by P4man on 2009-08-21
ive seen updates mute pcm channel for no reason. Its worth having a look, just run ```
alsamixer -c0
```

See if any channels are muted (use arrows to navigate.

---

### Post by SlugSlug on 2009-08-21
I remember my audio woes from days gone by, I used to uninstall pules and install oesound

---

### Post by AmyRose on 2009-08-21
Eh, I used to have problems like that, until I just gave up and removed PulseAudio. I wouldn't be the least bit surprised if it's the cause of your troubles.

---

