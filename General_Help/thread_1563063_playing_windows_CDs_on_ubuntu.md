---
title: "playing windows CDs on ubuntu"
date: 2010-08-28
forum: General Help
---

### Post by anarchjoem on 2010-08-28
I've been given a CD that runs on windows and discovered that it wouldn't work on linux. I have downloaded WINE but I am not sure what I should do next so that it runs. Apologies if I'm being really stupid here.
Joe

---

### Post by borth92 on 2010-08-28
need more info...what kind of cd....what is on the cd...

---

### Post by Dustin2128 on 2010-08-28
music, video, backups or software?

---

### Post by anarchjoem on 2010-08-28
it's actually a DVD oops sorry and it has a movie that I bought recently.

---

### Post by Dustin2128 on 2010-08-28
aaah, that clears things up, you just have to download the codecs. type (or copy/paste) this into the terminal.
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
then
```
sudo aptitude install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by Dustin2128 on 2010-08-29
did it work?

---

### Post by anarchjoem on 2010-09-01
Nope still can't get it to work:(

---

