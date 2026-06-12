---
title: "Master Volume Control in Alsamixer Doesn't control anything"
date: 2010-01-31
forum: General Help
---

### Post by gingivere0 on 2010-01-31
I'm a new Ubuntu user that switched from Windows XP a couple of weeks ago and this is my first post.  I am loving Ubuntu so far, but I do have a few problems.  One of these being that the master volume control in alsamixer doesn't control the volume of the sound coming out of my laptop speakers.  I've searched many threads in these forums and on google, but I just cant find the solution.  Can someone please help me?  Thanks in advance :)   

EDIT: I am using Ubuntu 9.10

---

### Post by gingivere0 on 2010-02-01
bump

---

### Post by pojr on 2010-02-01
I'm not exactly sure if this will work, because I'm having trouble with my volume too, but try this:

Go to
System > Preferences > Sound

The solution might be there.

---

### Post by gingivere0 on 2010-02-01
yeah I've read about doing that many times but every time I do, I don't see an option to switch channels.  When I use alsamixer from a terminal, I can hear that the PCM channel controls the actual sound coming out, and the Master Volume does nothing.  Thanks for the advice though. :)

---

### Post by gingivere0 on 2010-02-01
Ok, now, after switching to KDE desktop and the back to GNOME, my master volume controls sound, but the graphical sound control doesn't work.  By that I mean that when I try to mute the sound by using the volume meter in the GNOME panel, nothing happens.

---

### Post by gingivere0 on 2010-02-02
bump

---

### Post by warfacegod on 2010-02-02
Try removing it:

```
sudo apt-get purge gnome-media

sudo apt-get install gnome-media
```

---

### Post by gingivere0 on 2010-02-03
Nope, that didn't work, but thanks for the help :]

---

### Post by gingivere0 on 2010-02-03
bump

---

### Post by gingivere0 on 2010-02-04
bump
last one, please help!

---

