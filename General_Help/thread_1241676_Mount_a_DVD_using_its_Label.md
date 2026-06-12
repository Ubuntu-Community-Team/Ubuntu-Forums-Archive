---
title: "Mount a DVD using its Label"
date: 2009-08-16
forum: General Help
---

### Post by budo on 2009-08-16
Hello!
I'm wondering if there's a way to mount a DVD with its label, just like USB storage devices!
Trying to explain... now I can see "/media/cdrom" which is automatically mounted with the DVD filesystem, when I insert a DVD in the reader...
... but what I would like to obtain is to mount it in a directory named using it's label... so if the DVD has a label "MY_MOVIE_1" I would expect to find a dir "/media/MY_MOVIE_1" when it's mounted... Just like it happens for external USB harddrives...
... Do you think it's possible?

---

### Post by Tuvok41 on 2009-08-16
I'm running Ubuntu 8.04 Gnome desktop, and that is exactly how they get mounted, I see the label no problem. Is your version and desktop different then mine?

---

### Post by budo on 2009-08-16
> **Tuvok41 said:**
> I'm running Ubuntu 8.04 Gnome desktop, and that is exactly how they get mounted, I see the label no problem. Is your version and desktop different then mine?
No well... It's not a desktop problem... this is why I marked the thread with prefix "other" and not "gnome" or "ubuntu"... it's a "Linux" related problem in general.
I can see DVD Labels on gnome... the icon on the desktop... all ok.
But try opening that position... you'll see that the directory is always "/media/cdrom".
The behaviour is different if we're talking about USB devices (and not DVDs) since if you labeled your external HDD "MOVIES" it will be mounted on "/media/MOVIES".

The reason I'm trying to make DVDs be mounted in different dirs (automatilly) is to "workaround" a problem I have with a software... unfortunatelly this software is based on "dirnames" (mount point) to organiza your media... so if I have movies on different HDD there's no problem (the mount point is different because I labelled them differently) but when I have movies in DVD it cannot distingush one DVD from the other since they're always mounted in "/media/cdrom"...

I would like Linux to consider all my media (DVDs, HDDs etc...) in the same way: mount them in "media" using their label as dirname...

---

