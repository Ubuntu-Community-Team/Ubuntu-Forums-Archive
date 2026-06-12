---
title: "Asterisk users w/ Ubuntu 9.10 please chime in"
date: 2009-11-04
forum: General Help
---

### Post by sr_guy on 2009-11-04
There is a known bug with zaptel building with kernel 2.6.28. The patch is here:

[http://svn.debian.org/viewsvn/pkg-voip/zaptel/trunk/debian/patches/hrtimer_2628?view=markup&pathrev=6683](http://svn.debian.org/viewsvn/pkg-voip/zaptel/trunk/debian/patches/hrtimer_2628?view=markup&pathrev=6683)

But I am still unable to build zaptel under ubuntu 9.10. Is there a god script out there that will fix the zaptel timing issue? I would really like to get asterisk/freepbx functional under 9.10. Specifically, with zaptel, the SIT tone(s) that the freepbx callblocking fuction relies on zaptel timing. Any help is appreaciated.

---

