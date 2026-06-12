---
title: "Wtf   can't play  mp3's in Ubuntu"
date: 2010-03-18
forum: General Help
---

### Post by alanw8@oh.rr.com on 2010-03-18
Rhythmbox won't play mp3's and it says there is no available plug in. I can't seem to get any software in the software center. Everything I click on says not available in the current data. Please don't tell me I have to convert 3,000 files to .ogg. If linux is this lame I'm done before I even get started.

---

### Post by uRock on 2010-03-18
Open a terminal and install ubuntu-restricted-extras with this command.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by uRock on 2010-03-18
MP3 is a copyrighted format that Canonical can not ship with the Ubuntu install .iso.

---

### Post by Megafag on 2010-03-18
> **iRock said:**
> MP3 is a copyrighted format that Canonical can not ship with the Ubuntu install .iso.

If that is an IT crowd quote in your sig you messed it up ;)

also OP didnt rhythm box ask you if you wanted to install a plugin? mine did.

---

### Post by uRock on 2010-03-18
> **Megafag said:**
> If that is an IT crowd quote in your sig you messed it up

Which part? I have a hard time with his accent.

---

### Post by Megafag on 2010-03-18
> **iRock said:**
> Which part? I have a hard time with his accent.

Should read "Hello IT... Have you tried turning it off and on again?"

Also OP have you fixed your situation?

---

### Post by alanw8@oh.rr.com on 2010-03-19
My bad. I did an install in windows cause I didn't want to empty a parttion I use for backing up data from D. I don't want to re-size or create a new one. I have run into trouble with Gparted in the past and there is no room in the box for another drive. Anyhow I guess the install didn't finish right. I couldn't add a plugin or download new software.

---

### Post by oldos2er on 2010-03-19
Open a terminal (Applications, Accessories, Terminal), and run ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

This will install flash, java, mp3 and a few other codecs.

---

### Post by alanw8@oh.rr.com on 2010-03-20
OMG The 9.10 ISO I downloaded was damaged. I cleared a partion and installed 8.04 from a CD I had. This is fantastic. I was able to set up everything. The Alsa addon got my Klipsh surround working. The codecs installed for Rythumbox and I imported my music files. All of the OS updates installed and I have to say I can't believe the improvements since a couple years ago. This just might finally be the end of a long like-hate relationship with microsuck.

---

### Post by jsriz on 2010-03-20
> This just might finally be the end of a long like-hate relationship with  microsuck.Let us all refrain from using such language 
it is against the spirit of both Ubuntu.

p.s i personally hate windows....

---

