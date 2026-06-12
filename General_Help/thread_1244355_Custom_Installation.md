---
title: "Custom Installation"
date: 2009-08-19
forum: General Help
---

### Post by Elfo33 on 2009-08-19
I'm having a bit of trouble figuring out how to install packages not from the repository.

Essentially, I got annoyed at the kitchen sink approach of Ubuntu, and attempted to install just a few packages on top of a command-line installation.  However, since wicd, gnome-core, etc. are not on the Ubuntu DVD, I need to install them from a separate location.

I tried to download the debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) onto a flash drive, and install that way, but the base system complains that /media/FreeAgent/KINGSTON/ is not a valid location.

Could someone please walk me through, step by noob step, what I need to do?

---

### Post by Bachstelze on 2009-08-19
Why do you not want to install from the repositories?

---

### Post by Elfo33 on 2009-08-19
> **HymnToLife said:**
> Why do you not want to install from the repositories?

I would prefer to.  I don't have an ethernet connection here (rental), and so I need to use wireless.  The minimal installation doesn't include wireless, and so I need to install wicd (network-manager doesn't work for me).  HOWEVER, packages like gnome-core, wicd, etc. ARE NOT INCLUDED on the installation DVD, and without an already working internet connection, I can't download from the 'net.

So, I need pre-download these packages from the online repository, store them somewhere, and install from a not-already-approved source.  I just want step by step instructions for this, please.

---

### Post by P4man on 2009-08-19
Question has been asked often already. Here is a recent thread that should answer your questions:

[http://ubuntuforums.org/showthread.php?t=1235477](http://ubuntuforums.org/showthread.php?t=1235477)

---

### Post by Cheesemill on 2009-08-19
Are you installing from a Live CD/DVD by any chance?
 
If so then they don't contain any packages.
If you use the Alternate CD then you'll find gnome-core and wicd are on the disc (I'm pretty sure).

---

### Post by Elfo33 on 2009-08-19
I've tried both the LiveDVD and the alternate CD, using apt-cdrom add.  Neither one contains wicd, or gnome-core.  The only other packages I need initially are gdm and synaptic, with those four I can get online graphically.

Thank you for the link, I'll give it another shot.  I guess my Google-fu is lacking in finding resources if this has been asked so much :/

---

