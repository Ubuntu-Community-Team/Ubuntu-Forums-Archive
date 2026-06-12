---
title: "Play Music From Command Line????"
date: 2009-07-18
forum: General Help
---

### Post by Tman5293 on 2009-07-18
Hi,

I just wanted to know if there was a way to play music from the Terminal???

Any advice is appreciated.

---

### Post by The Tronyx on 2009-07-18
Playing music locally from the terminal is fairly straight forward and the methods for doing so have been addressed before, please see [http://ubuntuforums.org/showthread.php?t=513352](http://ubuntuforums.org/showthread.php?t=513352).

---

### Post by jerome1232 on 2009-07-18
My personal favourite is mocp, it wasn't listed in that thread that was linked.

---

### Post by cknight on 2009-07-18
There's also mplayer and mpc/mpd.  mpd is the music server and mpc is the client app which is controlled via the command line.

---

### Post by angry_johnnie on 2009-07-18
you could

```
sudo apt-get install sox
```

and then

```
play /some/music/file
```

works pretty good. :)

---

### Post by Tman5293 on 2009-07-18
mplayer works for me.

Thanks For The Help!!!  :guitar:

---

### Post by master_kernel on 2009-07-18
Also mpg123. But it seems like you settled on mplayer.

---

### Post by ~sHyLoCk~ on 2009-07-18
mpd + ncmpcpp

---

### Post by cabrey on 2009-07-18
You could use aplay to play single audio files. Or try moc (sudo apt-get / aptitude install moc) which is an ncurses based console player.

---

### Post by andrew.46 on 2009-07-19
Hi angry_johnnie,

> **angry_johnnie said:**
> 
```
sudo apt-get install sox
```


Ubuntu splits the SoX package up a little so you might be better to run:

```
sudo apt-get install sox libsox-fmt-all
```

and this should guarantee the *full* SoX experience :-).

Andrew

---

### Post by macjinlan on 2010-01-01
Hey everyone. My dummie question.
I'am using MOC console player, and i got question with sound change, in my KMix controller and MOC software.
When i trying to change sound in MOC, the "master" input in KMix controller bumping down or up, how i can fix this? I need only the players volume change, not general of my sound card configure. 

Thank you.

---

