---
title: "How do I upgrade my Ubuntu software to the latest versions..?"
date: 2010-02-13
forum: General Help
---

### Post by Pott on 2010-02-13
I have Rhythmbox 12.5 and I want 12.6: I have 62GB worth of music, all carefully tagged with album art and I want to be able to display it all :D

Is there a way to upgrade directly..? And how about all the other software? I'd love to always be kept up to date with the latest versions without having to uninstall/reinstall and redo the settings... if there's a way.

Thanks!

---

### Post by colobix on 2010-02-13
Update manager under system>admin will open up every time a new update is ready. With default settings only safe and tested versions will be updated.
If you want to update unsupported software, go to system>software sources and go to 3rd party software.

---

### Post by switch10 on 2010-02-13
```
 sudo apt-get upgrade 
```

will upgrade all packages.

---

### Post by Pott on 2010-02-13
Thanks. Did both of these, so I guess the latest Rhythmbox isn't in the repos yet. I'd checked through the Ubuntu software center and I had the same version as in there too.

---

### Post by colobix on 2010-02-13
> **switch10 said:**
> ```
 sudo apt-get upgrade 
```

will upgrade all packages.
He asked for an untested version of rythmbox.
He still needs to allow 3rd party sources to be updated inorder to update unsupported software using that command.

---

### Post by Pott on 2010-02-13
Is that in the 'Updates' tab, the prereleased updates (karmic proposed) tickbox? How safe is it to allow this..?

---

### Post by switch10 on 2010-02-13
yeah sounds like its not in the repo's.  YOu can go here [http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/](http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/) and install from source.  I don't know if this will keep your settings though.

If you have the album covers in each album's directory, and named folder.jpg, rhythmbox or any other media player will be able to use it.  I made a video yesterday actually here: [http://www.youtube.com/watch?v=gJqM9UPXjwA](http://www.youtube.com/watch?v=gJqM9UPXjwA)

Dave

---

### Post by Pott on 2010-02-13
Nah, every single one of my covers are embedded in the ID3 tag of each tune. It's alright though I'll wait for 12.6.

Getting the right music player has been a bit of a hassle... Media Monkey is perfect under Windows. Gmusicbrowser is so far the best one for Linux but I can't get it working under Conky. Rhythmbox is a bit simplistic but works well otherwise, and with conky.

---

### Post by oldos2er on 2010-02-13
If there's no PPA for the software you want, try its homepage: [http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)

Rhythmbox's latest stable version is 0.12.6; 12.6 is a very long ways away. :)

---

