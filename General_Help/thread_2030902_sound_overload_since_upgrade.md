---
title: "sound overload since upgrade"
date: 2012-07-21
forum: General Help
---

### Post by qwertyjjj on 2012-07-21
Ever since the upgrade to 12.04 and even 11.10, the sound on my laptop seems to eb seriously overloaded / distorting. I watch some sites like youtube and I have to have the volume turned all the way down to 1/10. Even I put it to 2/10, it starts distorting.
Any ideas what the problem could be?

---

### Post by jmfal on 2012-07-21
Hi     qwertyjjj

Open alsamixer and turn down pcm 

I,ve read an some laptops they had success turning pcm all the way down [00], but your headphone may become muted.

---

### Post by qwertyjjj on 2012-07-21
> **jmfal said:**
> Hi     qwertyjjj

Open alsamixer and turn down pcm 

I,ve read an some laptops they had success turning pcm all the way down [00], but your headphone may become muted.

Nope...turned it down to 0 but am still getting distortion.

---

### Post by jmfal on 2012-07-21
Have you edited the 
```
 /etc/modprobe.d/alsa-base.conf   
```

If you want to try this,open the file:
```
  gksudo gedit /etc/modprobe.d/alsa-base.conf   
```
And add this line to the end of file:
```
  options snd-hda-intel position_fix=1   
```
save/close to the "etc"folder .
Here is where I got the info
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by qwertyjjj on 2012-07-23
> **jmfal said:**
> Have you edited the 
```
 /etc/modprobe.d/alsa-base.conf   
```

If you want to try this,open the file:
```
  gksudo gedit /etc/modprobe.d/alsa-base.conf   
```
And add this line to the end of file:
```
  options snd-hda-intel position_fix=1   
```
save/close to the "etc"folder .
Here is where I got the info
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

Solved, thanks.
So what exactly does that do and what is the bug?

---

### Post by jmfal on 2012-07-23
I'm glad that solved you problem.
I know the link doesn't explain it very good, and to be honest with you ,, I can't explain it 
myself. sorry

If solved please marked solved using forum tools

---

