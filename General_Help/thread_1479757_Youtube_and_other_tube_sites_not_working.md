---
title: "Youtube and other tube sites not working"
date: 2010-05-11
forum: General Help
---

### Post by dmbolf on 2010-05-11
So I upgraded to 10.04, and now all my youtube videos now show up as "An error occurred, please try again later".  Then on other tube sites, or sites like stickam, they all don't load.  I've tried reinstalling all the flash plugins and such, but no luck.  Any help?

---

### Post by QIII on 2010-05-11
Rule out conflicts with swfdec and gnash by seeing if they are  installed.  If so, remove them.

How did you install Flash?

---

### Post by dmbolf on 2010-05-12
That fixed the problem, thank you very much!

---

### Post by smcvarno on 2010-05-16
That also fixed the problem for me. Having a quick look at what swfdec and gnash is (I am pretty much unfamiliar with these packages) it has left me wondering though what the impact of removing these packages may be?

From the sounds of it, swfdec should replace Adobe flash and enable the playing of embedded video's in its place. Have I got this right? 

If that is the case, would there be a way to reinstall swfdec and gnash and get them to play nice with adobe flash?

---

