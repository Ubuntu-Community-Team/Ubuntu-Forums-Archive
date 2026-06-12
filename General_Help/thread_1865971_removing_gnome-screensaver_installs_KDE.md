---
title: "removing gnome-screensaver installs KDE?"
date: 2011-10-20
forum: General Help
---

### Post by dncrews on 2011-10-20
I'm trying to get the screensaver working again after an upgrade to 11.10. This should be a straight-forward thing: just remove gnome-screensaver and install xscreensaver. The issue is that when I use

sudo apt-get remove gnome-screensaver

It says it'll remove gnome-screensaver and install probably a couple hundred components. It's trying to install KDE (sample components: akonadi, katepart, kde-runtime, kde-workspace, kscreensaver, plasma-desktop, etc).

Anyone know why it's doing this and what I can do to stop it? I'd rather not bloat my system with KDE stuff I'm not going to use just to enable my screensaver.

---

### Post by dncrews on 2011-10-31
So much for Ubuntu Forums

---

### Post by MG&amp;TL on 2011-10-31
Sometimes people slip through the net, y'know?

Have you installed xscreensaver yet? I think Ubuntu NEEDS a screensaver (as in, compulsory), and it tries to install KDE if no  alternative.

---

### Post by christopher.wortman on 2011-10-31
In all honesty, check out Kubuntu, you might like it.

Screensavers? I didn't know people still used CRT displays...

---

### Post by mcaltage on 2012-01-26
This worked for me.


Use synaptic.

Mark gnome-screensaver for removal and accept the new changes.

Go to Custom Filters > Marked Changes.

Unmark all of the new installs.

Apply.

---

