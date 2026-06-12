---
title: "Gnome ALSA Mixer"
date: 2011-03-20
forum: General Help
---

### Post by Voc on 2011-03-20
Hi, I am very new to Ubuntu (well, to Linux in general), and I am experiencing problems with the Gnome ALSA Mixer.  I installed Ubuntu on my MacBook Pro inside Windows (I am running Windows via bootcamp), and when I am running Ubuntu the sound doesn't work.  After researching the problem online, I was told that one needed to download an application called the "Gnome ALSA Mixer", and switch the mute to off (apparently the mute is default).  I downloaded the application, but whenever I try to run it the application window is blank.  There are no controls of any sort.  I was told when installing Ubuntu inside windows that the disk efficiency (I think thats what is was) is very much reduced, but I don't know if this has anything to do with that.

Also, is there a way to prevent the trackpad from registering stimulus while typing?  I find it very obnoxious that every time I try to type in my password or the like that the curser clicks off of where I'm typing, so I am constantly having to move the pointer back and re-click in the area I'm trying to type in (if that makes sense).

---

### Post by Krytarik on 2011-03-20
Try "alsamixer" of the package "alsa-utils", it fixed my issue with low sound.

Regarding the trackpad, see here:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by Voc on 2011-03-20
Thanks, but I have no idea what you mean by this:  "alsamixer" of the package "alsa-utils".  Where do I find this package?

---

### Post by Krytarik on 2011-03-20
> **Voc said:**
> Thanks, but I have no idea what you mean by this:  "alsamixer" of the package "alsa-utils".  Where do I find this package?
It's in the official repos, I could have mentioned it.
```
sudo apt-get install alsa-utils
alsamixer
```

---

### Post by Voc on 2011-03-20
Okay, I'll try that.  One more question though (about the trackpad):  the link you sent me lead me to another site that had a link to download what I believe is the trackpad software.  However, all I got was a bunch of weird symbols that looks suspiciously like when I try to run a Windows application on a Mac OS through textedit.  In other words, it was in a language that the Ubuntu I was running couldn't understand.  Is there another place I can get these drivers?

Other questions I have pertain more towards general (I guess that's what they'd be called) Mac drivers, particularly those for the cooling fan, keyboard backlight, and so on.  Is there any place I can go that might give me detailed information for running Ubuntu on a MacBook?

---

### Post by Voc on 2011-03-20
Okay, I got the trackpad driver to download through the mac side, and I transfered it to Ubuntu via a flash drive.  Unfortunately, the ALSA Mixer still draws a blank screen.

---

