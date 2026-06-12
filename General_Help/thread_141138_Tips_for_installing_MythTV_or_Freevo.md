---
title: "Tips for installing MythTV or Freevo?"
date: 2006-03-07
forum: General Help
---

### Post by gnomes on 2006-03-07
Hello.

I would like to get one of these PVR programs but I keep encountering problems with installing both of them. Freevo has issues regarding versions of Python and MythTV requires IVTV which also has issues with Ubuntu.

Do any of you have suggestions about getting one of these two programs operational, or perhaps could reccomend a similiar Linux distrobution with greater support for these programs?

---

### Post by andlinux21 on 2006-03-07
they have excellent HOWTO's as long as you have some of the supported hardware you should be able to get a box up and running.  I had to wait to get the right tuner card to even attempt to do MythTV. But i was able to watch TV on Breezy with my ATI Wonder card with no problems.

---

### Post by kzutter on 2006-03-07
I have two myth boxes, a backend and a frontend, both running on breezy.
IVTV drivers and lirc had to be manually complied and installed. The rest was available through apt repostitories. It was a lot of work (especially lirc) and I would think twice before doing it again. If you are not tied to ubuntu, then take a look at knoppmyth. It is a debian-based myth distro.

Good luck!

-Ken

---

### Post by chaumurky on 2006-03-07
I used the howto from here:

[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

Follow it in the right order and it's a piece of cake. lirc is still a pain though...

---

