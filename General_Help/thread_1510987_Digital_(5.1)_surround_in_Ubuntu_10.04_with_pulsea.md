---
title: "Digital (5.1) surround in Ubuntu 10.04 with pulseaudio?"
date: 2010-06-16
forum: General Help
---

### Post by Morientes on 2010-06-16
Hi

I would really like to get digital (5.1) surround in Ubuntu 10.04 with pulseaudio. However, when I go to the preferences->sound->hardware setting, I can only select analog surround outputs. The only digital outputs shown are stereo.
Anyone know if it is possible to get digital outputs?

---

### Post by fooman on 2010-06-16
in system > preferences > sound > hardware

at the bottom of that window, next to where it says "profile",  there should be a drop down menu with more choices.

EDIT,  never mind,  i see what you mean....only 2 digital choices,  and both are stereo.  sorry.

---

### Post by Morientes on 2010-06-16
> **fooman said:**
> in system > preferences > sound > hardware

at the bottom of that window, next to where it says "profile",  there should be a drop down menu with more choices.

EDIT,  never mind,  i see what you mean....only 2 digital choices,  and both are stereo.  sorry.

Exactly.
But thank you for the reply.

So, anyone know how to get the digital surround profiles?

---

### Post by Morientes on 2010-06-17
Anyone?

---

### Post by Morientes on 2010-06-21
Bump?

---

### Post by Morientes on 2010-06-24
Someone must know something about this?

If it's against the rules to bump threads, please tell me and I shall stop of course.

I would just really like a response to this...

---

### Post by elliotn on 2010-06-24
Ja the fact that 5.1 isnt there sux

---

### Post by Morientes on 2010-06-30
Sure does. But there's gotta be some way to fix it? Anyone?

---

### Post by KegHead on 2010-06-30
Hi!

Doesn't the mobo determine the audio?

KegHead

---

### Post by cbrunhaver on 2010-06-30
On my xbmc rig, I use alsa for an AC3 / DTS passthrough through an optical digital out.  I don't believe that Pulse supports this functionality because of it's mixing etc.

When I fire up alsa mixer, the name of my digital out was IEC958 and just make sure it is not muted.

-Chris

---

### Post by Neal121 on 2010-07-11
Hi Morientes,

Have a look over the attachments of this thread. It will surely help you upto some extent, as it helped me. ;)

[http://ubuntuforums.org/showthread.php?t=1353851](http://ubuntuforums.org/showthread.php?t=1353851)

Sorry for late reply.
I wasn't even on this forum when U posted UR problem... :o

---

### Post by lidex on 2010-07-11
Scroll down to 'Surround Sound' on this page:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")

Here's another:
[http://ubuntuforums.org/showthread.php?t=1491347]("http://ubuntuforums.org/showthread.php?t=1491347")

Also use gnome-alsamixer to make sure digital is enabled.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Morientes on 2010-07-27
Thank you for the replies. I will take a look at it.

---

