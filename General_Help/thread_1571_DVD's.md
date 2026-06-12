---
title: "DVD's"
date: 2004-10-21
forum: General Help
---

### Post by danip on 2004-10-21
I cannot seem to play dvds on ubuntu.  I try to play them with both vlc and totem and i get this error.

OSS device "dev/dsp" is already in use by another program.

---

### Post by im_ka on 2004-10-22
do you have any application running that uses the sound device?

---

### Post by danip on 2004-10-22
I dont have anything using it that i can think of.  I just pop the dvd in and the first thing i do is open up vlc or totem.

---

### Post by iarwaith on 2004-10-22
Largely appropriated from Debian Sound Wiki [http://wiki.debian.net/index.cgi?SoundFAQ](http://wiki.debian.net/index.cgi?SoundFAQ):

Try one of these:

/bin/fuser -v /dev/dsp
/usr/sbin/lsof|grep dsp

then kill off the identified process(es) with extreme prejudice (I just use a kill -9 after a ps aux) as long as they're not needed by something else you're using. 
I vaguely remember having this problem a couple of years back where Alsa was tying things up, so I uninstalled it and went with OSS [from memory]. This was more to save me stuffing around with working out the problem however, you may not wish to switch.

May be a bit extreme for your situation, but as for making this the default --freeing up sound on boot-- you could simply disable the service running that's tying up the dsp once you know what's doing it.

[/url]

---

### Post by danip on 2004-10-24
Well the first command worked the dvds play now.  Any idea how to pin point the thing thats using my sound on startup?

---

