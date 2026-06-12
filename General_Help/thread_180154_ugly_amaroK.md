---
title: "ugly amaroK"
date: 2006-05-21
forum: General Help
---

### Post by groggyboy on 2006-05-21
I run amaroK in gnome.  Awesome music player, but it sticks out like a sore thumb in my nice gnome environment.

Does anyone know how I could go about changing the theme that amaroK uses without actually installing kubuntu?

Something a little more like clearlooks-gperfection2?

cheers, groggyboy

---

### Post by adamkane on 2006-05-21
Install kubuntu-desktop or at least kcontrol.

Open kcontrol, and adjust the look of KDE apps.

---

### Post by groggyboy on 2006-05-22
worked like a charm.  thanks!

ugly amaroK no more!

8) 

groggyboy

---

### Post by aman_pervaiz on 2006-05-22
Just a question. On my system (inspiron 700m) amaroK runs terribly slow. For example if I want to jump to the next song and I press the next button on the gui, the player takes full 4 to 5 seconds before it decided to jump to the  next song. What goes on for 4 to 5 seconds, I have no idea. I like this player because it is highly customizable but why does it run so slow! Looks bloated or maybe I need to tweak some setting?

---

### Post by adamkane on 2006-05-22
Every new Ubuntu user needs to do this to get amaroK running smoothly:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686

``` 
AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

``` 

Remove dead entries from the GRUB menu:

```

update-grub

``` 
Reboot.

Enjoy the speed.

If you still have issues with amaroK playback on breezy, then install taglib-1.4 and alsa-oss. You have to search the forums for a copy of taglib-1.4 to download and install (or compile from source).

Let me know, if you have any questions.

---

### Post by aman_pervaiz on 2006-05-23
[QUOTE=adamkane]Every new Ubuntu user needs to do this to get amaroK running smoothly:

Intel Pentium:
```

sudo apt-get install linux-686 linux-headers-686

``` 
AMD K Series (Duron, Athlon, Sempron):
```

sudo apt-get install linux-k7 linux-headers-k7

``` 

Remove dead entries from the GRUB menu:

```

update-grub

``` 
Reboot.

Enjoy the speed.

If you still have issues with amaroK playback on breezy, then install taglib-1.4 and alsa-oss. You have to search the forums for a copy of taglib-1.4 to download and install (or compile from source).

Let me know, if you have any questions.[/QUOTE]

Thax for the reply. Tried your suggestion. Improves the speed but not by that much. Still takes two seconds for the song to change to next. 

*dumping amaroK and welcoming back the ever light weight xmms :-) *

---

### Post by nalmeth on 2006-05-23
Try listen or exaile for Gnome.

---

### Post by adamkane on 2006-05-23
Listen supporters always gotta horn in on the amaroK discussions.  :(

---

### Post by nalmeth on 2006-05-24
[quote=adamkane]Listen supporters always gotta horn in on the amaroK discussions.  :([/quote]
Damn straight. I love listen. It actually pick's up the right lyrics for my songs
I know this is just the lyric server, but leos.lyrics get's it right 95% of the time.

My only complaint about amarok. Otherwise, it's one of the first thing's I recommend to new linux users (with decent computers).

---

### Post by adamkane on 2006-05-24
The sad smiley looks more mad than sad.

---

### Post by groggyboy on 2006-05-25
I tried listen (and exaile - but that one is just a little too bleeding-edge for me).

I keep a copy of listen on my laptop (and a copy of xmms for rare occasions), but my main music player is definitelty amaroK.

I appreciate some features of listen.  The GUI is well-done, except for a few minor annoyances (like the middle column).   The Last.fm pane, where you see a rating of similar artists, is fun.  The dynamic playlist mode is really neat too.

But I feel that listen's shortcomings overpower its pluses.  Where's the equalizer?  Or the support for portable media players?  How about support for libvisual or xmms visualizations?  Not to mention the horrible way that listen handles the media library.  Every time I add a song or album to my music folder, I have to manually tell listen to look for it.  Not by selecting refresh library or reload library from the menu (which would seem intuitive), but by telling it to import the ~/music directory all over again (which fortunately doesn't take as long as it does on the first go)!

So amaroK may be ugly with its non-gtk-native user interface, but at least it does what I want it to do, the way I want it done.  And with the trick mentioned in this thread, even the ugly UI can be overcome!

So quit telling me to try listen.  I did, and I think it sucks.

groggyboy

---

