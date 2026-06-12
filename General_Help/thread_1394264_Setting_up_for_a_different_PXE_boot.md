---
title: "Setting up for a different PXE boot"
date: 2010-01-30
forum: General Help
---

### Post by Gremnon on 2010-01-30
I've looked at the available support info on PXE booting, and it helps - to a point.
However, like all PXE boot guides I've read, it assumes you're installing the same system you're working on, which I'm not.
I've been asked to set up a Gentoo Linux box. I don't have a Gentoo install to hand to follow the Gentoo guides for PXE booting, all I have available is a single Xubuntu box, that I'm not willing to wipe.
So I'm trying to figure out, how exactly to get a PXE boot to work, so I have the equivilent of the Gentoo Minimalist CD, over a PXE boot?

And yes, I have asked at the Gentoo forums. They gave me Gentoo-from-Gentoo guides which don't help at all.

---

### Post by cariboo on 2010-01-30
Have you tried the Gentoo instructions? If you haven't tried them substitute apt-get install for emerge. Linux is Linux, the only real difference is package management.

---

### Post by Gremnon on 2010-01-31
I beg to differ - Gentoo seems to refer extensively to /etc/conf.d - a directory I've never once found existing on any Ubuntu install to date.
That aside, I have tried the Gentoo instructions, one of which refers to 'File=Slurp' which appears to be conspicuously missing from the Ubuntu repositories - unless that's just because I'm on Jaunty instead of Karmic after a bad experience with Karmic.
The only other instructions I've had all rely on the previously mentioned /etc/conf.d, which is inconvenient when you have no idea where the files it refers to are meant to be on a Ubuntu system.

---

