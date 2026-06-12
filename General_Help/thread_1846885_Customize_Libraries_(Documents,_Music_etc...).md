---
title: "Customize Libraries (Documents, Music etc...)"
date: 2011-09-19
forum: General Help
---

### Post by JMT391 on 2011-09-19
I dual boot win7 and ubuntu natty on two separate HDDs.  I have a third HDD I would like to use as a shared storage drive so I can keep my music and document libraries consolidated across both OS's.  In win7 you can choose the paths for documents and music and whatnot - can you in ubuntu?  In other words I want my documents/music/whatever folders in my home folder to point to the ones on the other HDD.  Possible?

---

### Post by josephmills on 2011-09-19
> **JMT391 said:**
> I dual boot win7 and ubuntu natty on two separate HDDs.  I have a third HDD I would like to use as a shared storage drive so I can keep my music and document libraries consolidated across both OS's.  In win7 you can choose the paths for documents and music and whatnot - can you in ubuntu?  In other words I want my documents/music/whatever folders in my home folder to point to the ones on the other HDD.  Possible?

yes you can use the mount command to mount it where-ever. 
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by JMT391 on 2011-09-20
Okay, so I tried to do that using pySDM (set the mountpoint to /home/*user*) so that it mounts there at bootup time.  Worked successfully, but after restarting I lost my desktop environment - my unity launcher, indicator applets, desktop background, any folders on my desktop, etc... were all reset.

On top of that, I was getting no sound.  Gnome device manager showed proper detection of the soundcard, but the sound indicator showed up as "label empty."  If I do not mount at boot time, everything resets.  I did notice that when I mounted the extra drive to /home/*user*, ubuntu created a the same set of hidden files/folders it creates in the home folder normally.

Why is it creating a new desktop environment when I do this?

---

