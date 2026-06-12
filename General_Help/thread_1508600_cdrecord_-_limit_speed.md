---
title: "cdrecord - limit speed ??"
date: 2010-06-13
forum: General Help
---

### Post by FunkyRes on 2010-06-13
My DVD player attached to my TV is picky.

Burn CD's (with avi files) at 8X and it plays them. 16X and it complains about bad disk. Every time.

In karmic, I can only get cdrecord to burn at 16x.

Here's the command:

cdrecord -dev=/dev/scd0 -speed=8 -dao -pad -v something.iso

and it burns at 16x instead of 8x. Command issued with root privilege.

Identical hardware under CentOS 5.x and it burns at 8x, like I asked it to.

I'm all SATA if it matters.
What do I need to do to get the version of cdrecord with karmic to burn a data CD at 8x? For whatever reason, CDs burned at 16x just don't work in the DVD player attached to my TV.

---

### Post by FunkyRes on 2010-06-13
Nevermind, the sensitivity to speed I was remembering was with DVD, not CD - and burn speeds are the same regardless of OS, 16x for CD works but DVD has to be kept at 8X.

---

