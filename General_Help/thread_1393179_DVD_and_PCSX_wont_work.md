---
title: "DVD and PCSX wont work"
date: 2010-01-29
forum: General Help
---

### Post by sleepystoner420 on 2010-01-29
basicly my dvd's either dont play at all or they play without sound which is really wierd im not even sure where to begin on that

and as for my PCSX it gets to the playstation logo screen but it freezes and the only way i can close it is by login out of my account and back in i've done lots of research and no1's come across this problem atleast from what i saw searching for an answer (for 2 days)

i've only had linux for 4 days so im not to familiar with anything

---

### Post by raktarok on 2010-01-29
I don't know anything about the playstation thing, but for dvds, try adding the mediubuntu repository and installing libdvdcss2 package. Enter these in the terminal:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install libdvdcss2
```

Also, which player are you using? Try something like vlc.
```

sudo apt-get install vlc
```

---

### Post by sleepystoner420 on 2010-01-29
Thx! that worked perfectly mixed with the VLC app now if only i could fix the PCSX lol but thanks a bunch!

---

