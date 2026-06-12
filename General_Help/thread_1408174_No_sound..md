---
title: "No sound."
date: 2010-02-16
forum: General Help
---

### Post by Len Tyree on 2010-02-16
Unable to get any sound out of the system from anywhere, not from movies or inputs on either Yahoo or firefox, and not from music cd's inserted into the cd players??

Had good sound a few days ago??

Looked at all things concerning sound within the system and unable to find anything that looks like it may be causing a problem.

Upgraded Rhythmbox, also Firefox, no help.

Any help would be appreciated.

Thanks, Len Tyree.[IMG]http://home/len/photo/DALE genius at work[/IMG]

---

### Post by lovinglinux on 2010-02-16
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Len Tyree on 2010-02-17
Thanks to lovinglinux.

I looked at the sound trouble shooting site, but could see nothing that may help.

When I boot up the system, and when I shut down, the speakers make a sound, but at no other time.  So I think the speakers are ok and connected properly.

I am now going to reload from my latest back-up and see what happens.  Could be the latest fix sent in by Linux caused a problem.

Thanks, Len Tyree.

---

### Post by MinimalBin on 2010-02-17
Open *alsamixer* and see if *Master* and *PCM* are both pulled up and not muted (* MM* ).

---

### Post by Len Tyree on 2010-02-18
For MinimalBin, or anyone:

alsamixer??  Don't know but maybe this.

Clicked on systems>preferences>sound, returned a screen named 'sound preferences' with headings of 'sound effects, hardware, input, output and applications'.
If this is what you are talking about (hopefully), everything there is set up and looks to be running fine, no muting.
Also reloaded system from back-up usb drive, no help.
Then used apt-get to upgrade alsamixer; updated a lot of firefox units, (and others), too many to count.
Still no help.
Guess next thing is new sound card, if I can find one here where I live.
Will keep all updated.

hanks, Len Tyree.

---

