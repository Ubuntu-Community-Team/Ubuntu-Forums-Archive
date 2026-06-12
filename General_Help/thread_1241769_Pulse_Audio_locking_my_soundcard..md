---
title: "Pulse Audio locking my soundcard."
date: 2009-08-16
forum: General Help
---

### Post by Cygoku on 2009-08-16
Using Jaunty, pulseaudio is locking my soundcard under my DELL Inspiron 6400.  

System >> Preferences >> Sound and changed Autodetect to OSS and still no luck (Alsa aswell).  

I thought of uninstalling PulseAudio using Synaptic, but it seem that it will also completely remove the Ubuntu Desktop.  

What else can I try ?? 

Cygoku

---

### Post by VipX1 on 2009-08-16
I put Ubuntu on my brothers Inspiron 6400 last night with no problems and I watched a few Videos on you tube when I installed Flash 10 so I did have the sound OK. What are the symptoms of the problem. If you want I'll start up my brother's Inspiron again and tell you what settings are in it if that helps..

---

### Post by VipX1 on 2009-08-16
DELL Inspiron 6400
HDA Intel STA9200
No proprietary drivers in use.
Sound Capture is ALSA, Playback - all set to autodetect.

---

### Post by Cygoku on 2009-08-17
Open the laptop, use synaptic the install emesene, mplayer-nogui and gnome-mplayer

# sudo apt-get install emesene mplayer-nogui gnome-mplayer

Once those are isntall, try to mess a bit with them, you'll eventually lock the sound card.  

Then go to System >> Administration >> System Monitor, kill the pulseaudio process and you will get sound back.  

Cygoku

---

### Post by CatKiller on 2009-08-17
> **Cygoku said:**
> it seem that it will also completely remove the Ubuntu Desktop.

It won't. *ubuntu-desktop* is a meta-package that depends on all the things in a default Ubuntu install. Since PulseAudio is included in a default Ubuntu install, removing it means that you no longer have all of a default Ubuntu install. So the *ubuntu-desktop* package has to go.

---

