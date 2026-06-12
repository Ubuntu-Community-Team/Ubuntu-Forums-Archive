---
title: "No sound with videos / movies"
date: 2006-05-03
forum: General Help
---

### Post by rez on 2006-05-03
Hey ya'll,

Recently installed the w32codecs and was enjoying being able to watch whatever formats I wanted successfully under Ubuntu.  Previously, all I got was audio and now video.  Everything was fine until what I think I did was a simple reboot (or boot up the next day).

Unfortunately, my problem is now reversed.  I have video, but no sound when playing.  I've tried a number of players (Mplayer, xine, Totem, Kaffeine etc.) but all have the same result - picture, no sound.

I can play mp3s fine, so I'm assuming my soundcard and drivers are working fine.  The volume is up in the players and mute isn't selected.

Any ideas peeps?

---

### Post by noxious on 2006-05-03
Try this:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

restart firefox

---

### Post by rez on 2006-05-03
Sorry, I'm talking playing vids outside Firefox ... stand-alone player.

Tried that anyway, still no luck :(

---

### Post by Kobalt on 2006-05-03
Did you install/remove anything after installing w32codecs and before your reboot, any updates ? Did you check your gstreamer plugins as well ?

---

