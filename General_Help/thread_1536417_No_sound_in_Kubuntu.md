---
title: "No sound in Kubuntu"
date: 2010-07-22
forum: General Help
---

### Post by akssps011 on 2010-07-22
Hi

I am using Kubuntu 10.04

When I play any media file, I am not able to hear any sound. 
A few weeks ago, except DragonPlayer and Amarok no other app on my system was able to play sound(vlc etc. ) . A few days ago, even they stopped working and I saw a message related to Phonon and HDA Intel card of my system that it is not working properly.

I also have dual boot with winXP and it sound play very well on it.

Searching the net, I have tried these:
```
/usr/sbin/hwinfo --sound
```
It says no such file or directory

```
alsamixer
```
It gives the following:

[IMG]http://picasaweb.google.com/lh/photo/Md6vzZRMMKKAU2URYSa4pA?feat=directlink[/IMG]

In case above image doesn't show up:
[http://picasaweb.google.com/lh/photo/Md6vzZRMMKKAU2URYSa4pA?feat=directlink](http://picasaweb.google.com/lh/photo/Md6vzZRMMKKAU2URYSa4pA?feat=directlink)

Please help.

---

### Post by pushkarajthorat on 2010-07-26
try changing the preferred device in system settings -> multimedia.

---

### Post by Zorgoth on 2010-07-26
I can't see your alsamixer photo because my work net nanny blocks it.  Are PCM, Speakers, Headphones, and Master all unmuted and set to 100?

---

### Post by lidex on 2010-07-26
Try increasing PCM level.

---

### Post by pushkarajthorat on 2010-07-27
> **Zorgoth said:**
> I can't see your alsamixer photo because my work net nanny blocks it.  Are PCM, Speakers, Headphones, and Master all unmuted and set to 100?

here i am uploading it for you, I see the PCM is muted, maximize it.

---

