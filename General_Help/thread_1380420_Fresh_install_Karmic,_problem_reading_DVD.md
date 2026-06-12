---
title: "Fresh install Karmic, problem reading DVD"
date: 2010-01-13
forum: General Help
---

### Post by 2blue on 2010-01-13
I have had a new install of Karmic from CD and have done all updates and added a few applications like VLC and a few others. 


I have several different media players, Totem, VLC, Xine, and gxine. 
I started out thinking Totem might be enough, but added VLC as it can handle just about anything, and then the other just to see of any thing happened. 

I have installed all restricted and unrestricted packages from the Medibuntu depositories I can find. Still my laptop will not read any kind of DVD. I am region 2, but have tried both bought region 1 and region 2 DVDs. I had this problem last time I installed Ubuntu, but after installations of a few  applications and messing about it suddenly worked. I really didn't know why or what suddenly was working.  

I've been working on this problem for days now. What could be missing?

---

### Post by Is Mise on 2010-01-13
```
sudo apt-get install libdvdread4 && sudo /usr/share/doc/libdvdread4/install-css.sh

```
Have you tried running this?

---

### Post by 2blue on 2010-01-13
Thanks for your tip

I ran your command, but I think I already have tried that one too, at least no improvement.  I have seriously been at this for a while now.  When I install a DVD the computer gets very active, and tries and retries reading, but fails mounting. I get this message from VLC:

Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'.

I have a Fujitsu Amilo, and my DVD rom is very stubborn.

---

### Post by Is Mise on 2010-01-13
Do you have trouble reading data DVDs as well as movies?

---

### Post by patros on 2010-01-13
Check out [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by 2blue on 2010-01-13
I've spend hours on that page, and installed every possible package. My computer seams to read data DVD and plays regular CD's.

---

### Post by Is Mise on 2010-01-13
Have you tried playing the DVD with MPlayer? I remember having a DVD that wouldn't play in the other players but worked OK with that.

---

### Post by 2blue on 2010-01-13
I've tried MPlayer. I'm not testing out a difficult DVD or something found on *******. Not any standard DVD are recognized at all.

---

### Post by jed4czar on 2010-01-30
Any progress with this?

I don't know if I've had this problem for long as I usually only download and burn avi files and watch via VLC. Just tried a DVD rental and wont play! Tried a few actually no conventional DVD (vob) movie will play. In fact it wont even mount the disk. 

# mount /dev/scd and mount /dev/sr0 returns "no medium found on /dev/sr0. I see the light flashing on the front of the drive as it trys. It will read data no worries and even play avis from there. 

fstab line is: /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Upgraded to Karmic in November. Any help would be appreciated.

---

### Post by coldraven on 2010-01-30
It seems to me that you need to borrow an external DVD drive and if that works then there must be a fault in you internal one.
It might be quicker! :p

---

