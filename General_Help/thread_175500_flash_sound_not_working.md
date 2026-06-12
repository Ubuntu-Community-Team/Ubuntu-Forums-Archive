---
title: "flash sound not working"
date: 2006-05-13
forum: General Help
---

### Post by twirp on 2006-05-13
The sound in flash isn't working (this is mainly for my brother, so I don't care).
But I followed a direction on another post about creating a folder or something like that, and it doesn't work...
So I was wondering if anyone has got sound to work in flash yet (the macromedia one... (i think that's how it spelt))
I'm using Opera and FireFox as the browsers, FireFox is 1.5.3 (or something) and I downloaded the installer from marcromedia.  It will show stuff, but there's no sound.
There's sound for music and videos (avis, mp3s, etc) but not flash...

Thanks for your time.:-k

---

### Post by Sef on 2006-05-13
In Gnome, Applications > Accessories > Terminal

In the terminal, type these two commands

sudo apt-get update

sudo apt-get install alsa-oss

---

### Post by twirp on 2006-05-16
Is there anything else I can try?
It still doesn't work.

---

### Post by enopepsoo on 2006-05-19
[QUOTE=twirp]Is there anything else I can try?
It still doesn't work.[/QUOTE]

I am reporting the same problem.  Maybe we should do a bug report buddy. :???: 

or try ```
sudo killall esd
```
perhaps?

---

### Post by Rui Pais on 2006-05-20
hi,
have you tried to do (after install alsa-oss):
```
sudo gedit /etc/firefox/firefoxrc
```
Find the line with FIREFOX_DSP and replace it to:
> FIREFOX_DSP="aoss"

That worked for me.

---

### Post by GeneW on 2006-05-20
The only thing that worked for me is starting firefox like this "aos firefox".

---

### Post by Rui Pais on 2006-05-21
[QUOTE=GeneW]The only thing that worked for me is starting firefox like this "aos firefox".[/QUOTE]
hi, do you mean:
```
aoss firefox 
```

;)

---

### Post by GeneW on 2006-05-21
[QUOTE=Rui Pais]hi, do you mean:
```
aoss firefox 
```

;)[/QUOTE]

Yes, sorry.

---

### Post by ketsugi on 2006-05-22
Thanks, this fixed my Flash sound problem.

---

