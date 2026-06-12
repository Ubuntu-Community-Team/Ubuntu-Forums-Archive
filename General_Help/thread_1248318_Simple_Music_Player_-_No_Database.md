---
title: "Simple Music Player - No Database"
date: 2009-08-24
forum: General Help
---

### Post by Olmy on 2009-08-24
I'm looking for a simple, solid music player - I know there have been many threads on this but none quite seem to cover what I want...

1/ Must Play FLAC.

2/ Must **NOT NOT NOT** force me to import my files into some sort of database - my music is organised quite well enough in the file systems of removable storage. If it has such a facility I want to be able to ignore it. This rules out rhythmbox (as far as I can see) et al. Just want to navigate the file system and play a directory of files.

3/ Would like an equalizer and perhaps a simple visualization.

Potamus is nearly there but lacks an equalizer. I thought VLC was just the job until I re-organised the play list display and was never able to access it again.

---

### Post by credobyte on 2009-08-24
mp3blaster ( available from repos ) :guitar:

---

### Post by jesuisbenjamin on 2009-08-24
Did you try Audacious? It's quite good. Don't know about FLAC though.

---

### Post by nothingspecial on 2009-08-24
cmus is a commandline music player. Very simple.

or mplayer which you should already have. Just type ```
mplayer path/to/music_file
```

---

### Post by Olmy on 2009-08-24
Thanks for the replies!

Audacious looks to be what I want..... BUT.....

I had a problem with my sound skipping and had to add a .asoundrc file to fix it (works for all the other players I've tried). Seems like this player is ignoring it and I've upped its own buffer to 10000 and it's still skipping...

Gerrrr....

---

### Post by jesuisbenjamin on 2009-08-24
You should make a new thread with this issue, there is surely a solution available.

---

### Post by Olmy on 2009-08-24
QMMP seems to fit the bill (well, it works). Don't like the gui - it's tiny on my netbook and it seems to get confused and re-arrange itself on close/open all too often - bits of it all over the desktop.

jesuisbenjamin, I raised the general sound problem and didn't get much of a response - found the answer myself in the end (and still don't understand it).

I assume Audacious is using a different sound system - the sound in ubuntu seems well confusing. It does to a newbie like me, anyway....

---

### Post by jesuisbenjamin on 2009-08-24
Hi Olmy,

Don't get desperate. I never got any issue with Audacious except after some upgrade. You may find an answer soon, possibly on another forum. I am sorry i can't help you with that.

---

### Post by MickS on 2009-08-24
I agree with you I find the whole playlist thing annoying, that's the main reason I abandoned Amarok in favour of VLC. Your best bet I would have thought is to fix VLC. When I had a similar problem after messing about with themes I fixed it by finding the config file and deleting it, that puts VLC back into it's default setting and it generates a new file.
Sorry can't remember where the file was but a bit of searching will reveal it.


Mick

---

### Post by Olmy on 2009-08-24
MickS, Yes I quite liked VLC but all I did was open the playlist, add the track number, put it as the first column and order on it.

I never saw the playlist again - every time I tried to open it, VLC just closed.

I did think of trying to delete the config file but I posted this instead.

jesuisbenjamin, I'll try another post in multimedia, or maybe here? The responses seem better here....

I'm staying reasonable patient - I'm an old windoze hack but I thought a completely broken xp install on my netbook was a good excuse to try ubuntu. I want music going soon however, as I'm off on my hols and want to use it.

I can live with QMMP unless it does something else nasty - listening to it now...

---

### Post by L_V on 2009-10-11
qmmp is fine.

However qmmp available in Debian repos is better (version 3.0-3) (easier to manage skinning).

Does somebody know why qmmp  V 2.3 is still in Karmic repos ?

---

### Post by tgalati4 on 2009-10-11
sudo apt-get install moc

Go into your music directory:

mocp

---

### Post by L_V on 2009-10-13
Qmmp V3 can be found in PPA here:

[https://launchpad.net/~stiff.ru/+archive/ppa](https://launchpad.net/~stiff.ru/+archive/ppa)

---

### Post by L_V on 2009-10-16
Finally **Juk** is not so bad, and very light.

---

