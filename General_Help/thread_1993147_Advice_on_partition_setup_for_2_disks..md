---
title: "Advice on partition setup for 2 disks."
date: 2012-06-01
forum: General Help
---

### Post by ShaneR on 2012-06-01
Hey, Folks.  Decided to come back to Linux simply for a change. A Little out of practice, so...

I'll be installing on a system with 2 physical disks and I'd like some advice on the best way to set these up given this:

I'll be running Windows in virtualbox as I need to use Adobe products (I'm a photographer) and my photo files will be taking up the vast majority of my disk space.

Ideally, I'd like linux to live on all (or part) of the first disk and have Virtualbox (somehow) use the second for VB's virtual disk.

Thanks. :)

---

### Post by Irony on 2012-06-01
That's the set-up I have - I have a second disk formatted as ext 4 and set up a folder in it to which I installed windows in virtualbox. Can't remember the details but just choose where to install your windows and it will install into a file with an extension .vdi.

---

### Post by ShaneR on 2012-06-01
Thanks, Irony.  I figured it out.

The "mount point" was messing me up during the install process (I didn't think I needed one).  I finally clued in to name it whatever I wanted and go on.  I guess I was expecting it to act like Windows and just show up as an empty data drive and only formatting required (not setting a mount point as well).

Anyway, like I said, I'm out of practice. ;)

---

