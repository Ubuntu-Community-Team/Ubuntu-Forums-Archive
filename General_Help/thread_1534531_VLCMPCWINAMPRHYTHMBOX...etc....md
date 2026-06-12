---
title: "VLC/MPC/WINAMP/RHYTHMBOX...etc..."
date: 2010-07-19
forum: General Help
---

### Post by bocaccio on 2010-07-19
Ok on windows; yuck i know how you all hate that word. Now i wanna break all the windows; joke.
 
I used vlc, media player classic, and winamp, on an occasion itunes but desperately wanted another way to sync my nano..
 
I finally got vlc on ubuntu and use rhythm box; so what else has all the needed codecs and works well? The standard movie player is not a great one.
 
I guess just asking what do you all use.

---

### Post by kerry_s on 2010-07-19
all you need to do is install "**ubuntu-restricted-extras**".

if you want **w32codecs** & **libdvdcss2** you need to add the medi repos.

```


sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


```

w32codecs is like what you install in windows
libdvdcss2 is for dvd playback

i use gnome-mplayer for everything.

---

### Post by bocaccio on 2010-07-19
Your the ****!!! Thanks man!! :KS

---

