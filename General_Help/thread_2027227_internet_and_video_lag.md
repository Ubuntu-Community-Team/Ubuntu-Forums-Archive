---
title: "internet and video lag"
date: 2012-07-16
forum: General Help
---

### Post by The musmula on 2012-07-16
I have just installed ubuntu 12.04 with cd, manually, means, I made an ubuntu partition alongside windows, I made a 2.5 GB Swap partition (because I have 1.2 GB of RAM), I have a second hard disk drive of 10 GB and I made that to my home folder.

everything works perfect, but, there is always a "but", I tried to play a 5 minutes HD movie, which I made by myself, and it displayed just a white screen and played the sound.

I fixed that almost by inputing into terminal ```
sudo apt-get install ubuntu-restricted-extras
```

but it still lags and every 5th picture is blank

then I saw that my internet lags the same way, when I scrol down every 3th picture is blank so it makes a unusual effect, actually I saw that before but I had no explanation, please HELP[-o<

---

### Post by evilsoup on 2012-07-16
Not sure about the internet - do you mean internet video? Or webpages generally? If  the former, it's probably problems with your flash player plugin (I've heard good things about the 'flash-aid' add-on for firefox). If it's webpages generally, maybe try a different, more lightweight browser like chromium or midori (or google chrome - it isn't in the repositories, but google are committed to support flash - the trade-off being google's tracking stuff).

With the movie you created yourself - is this a .MOV from FCP? There doesn't seem to be much support for the big, uncompressed .MOV files, even VLC doesn't really play them properly. I've had some luck playing them with avplay (a part of the avconv tools); this goes through any media file I've thrown at it like a hot chainsaw through butter, but it's only a commandline tool. Maybe mplayer can also do it. Or alternatively, you can try converting it to some other format.

I hope that helps.

---

### Post by The musmula on 2012-07-16
> **evilsoup said:**
> Not sure about the internet - do you mean internet video? Or webpages generally? If  the former, it's probably problems with your flash player plugin (I've heard good things about the 'flash-aid' add-on for firefox). If it's webpages generally, maybe try a different, more lightweight browser like chromium or midori (or google chrome - it isn't in the repositories, but google are committed to support flash - the trade-off being google's tracking stuff).

With the movie you created yourself - is this a .MOV from FCP? There doesn't seem to be much support for the big, uncompressed .MOV files, even VLC doesn't really play them properly. I've had some luck playing them with avplay (a part of the avconv tools); this goes through any media file I've thrown at it like a hot chainsaw through butter, but it's only a commandline tool. Maybe mplayer can also do it. Or alternatively, you can try converting it to some other format.

I hope that helps.

well, I use google chrome as my web browser and the video was a .avi and before, in the times when I installed ubuntu via wubi, there was no problem with .avi files.

---

### Post by evilsoup on 2012-07-16
Hmm. Maybe try different media players? VLC uses a different back-end than Totem, maybe that will work.

Maybe your computer is having trouble with Unity? It's *slightly *on the resource-intensive side of things, what with all the 3D compositing. Try using Unity 2D instead (on the login screen click on the little wheel & select 'Ubuntu 2D').

---

### Post by The musmula on 2012-07-16
thanks, I tried allready VLC but who knows...

I SOLVED IT!!!!!!!!!
I installed SMPlayer and... IT WORKS!
I have no more problems with .avi files.
=D>=D>=D>=D>

---

