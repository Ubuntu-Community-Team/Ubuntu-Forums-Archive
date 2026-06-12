---
title: "Dying for banshee to work."
date: 2006-02-26
forum: General Help
---

### Post by Sewage on 2006-02-26
For some reason I can't get banshee to work correctly.

I finally, after a lot of work got it running, only... poorly. It doubles songs a lot, crashes when uploading new songs sometimes, completely crashes when I plug in my ipod, and won't start up at all if the pod's already plugged in.

I have no idea what could be causing it, not sure where to begin to understand this. It's a good looking program and I've heard good things, I just wish it would work.

---

### Post by aysiu on 2006-02-26
Did you install it through the repositories or from source?

You can always try deleting your Banshee profile. I think it lives in /home/username/.banshee

---

### Post by Sewage on 2006-02-26
Well, I did it though a deb, I had to fill in some files though.

Also, I've found an error in terminal when opening it~ I can't copy paste this moment, but it basically said it wanted dbus 39 and all I had was dbus 38...

I went and installed dbus 61 I thought... Ah, this is confusing.

---

### Post by Sewage on 2006-02-26
Oh, that error only shows if my ipod is plugged in by the way.

---

### Post by closeyourwindows on 2006-02-26
I got mine to work just fine, but I installed it using apt-get.  I would uninstall it a do a locate banshee and delete all entries then use the repositories to install it.  I know how  you must feel, I was addicted to amarok until I found banshee.

---

