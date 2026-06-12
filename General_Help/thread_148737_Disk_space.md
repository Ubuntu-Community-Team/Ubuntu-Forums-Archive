---
title: "Disk space"
date: 2006-03-22
forum: General Help
---

### Post by terranz on 2006-03-22
I have just used the Automatix script because it looked like and easy way to get what I haven't already.

It broke openoffice but The problem for this thread is that I can no longer log in as me and I get an error that my disk is full.

Can someone give be advice on what I can get rid of to free space?
Everything is in one partition except /home
Can I create another partition an move /usr or some such onto it?

I have a screen grab attached (logged in as root)

---

### Post by az on 2006-03-22
[QUOTE=terranz]I have just used the Automatix script because it looked like and easy way to get what I haven't already.

It broke openoffice but The problem for this thread is that I can no longer log in as me and I get an error that my disk is full.

Can someone give be advice on what I can get rid of to free space?
Everything is in one partition except /home
Can I create another partition an move /usr or some such onto it?

I have a screen grab attached (logged in as root)[/QUOTE]
You left 2.9 gigs for "/".  Holey moley!

You need to boot a live cd (or the installer) mount the partition and delete stuff from /tmp.  You can also delete the debs in /var/cache/apt/archives.  That may buy you some space.  If you are really desperate for space, delete the larger (older gzipped) logfiles.

---

### Post by terranz on 2006-03-22
Thanks for the info, I'll try the packages.  Tmp is only a few megs.

If this was windows I'd just edit a few system paths and move something like program files to another partition and/or do some resizing.

---

### Post by taurus on 2006-03-22
You can resizing too with gparted!!!

---

### Post by terranz on 2006-03-22
is that safe resizing?

In the past I've used partition magic and linux has thrown a hissy fit at me (kernel panic)

---

### Post by terranz on 2006-03-22
[QUOTE=azz]You left 2.9 gigs for "/".  Holey moley!

You need to boot a live cd (or the installer) mount the partition and delete stuff from /tmp.  You can also delete the debs in /var/cache/apt/archives.  That may buy you some space.  If you are really desperate for space, delete the larger (older gzipped) logfiles.[/QUOTE]

I freed 560MB+ from /var/cache/apt/archives

---

