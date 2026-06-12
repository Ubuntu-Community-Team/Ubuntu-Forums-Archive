---
title: "imagemagick, lcms and Ubuntu"
date: 2012-02-02
forum: General Help
---

### Post by nateswitch on 2012-02-02
I have a server running 10.04 LTS.  A piece of software we're running now requires imagemagick with lcms support.  

How can I determine if the copy of imagemagick I've got installed currently has lcms support enabled, and if not, how do I get imagemagick with lcms support installed?  Is there a package in the repository, or do I need to build it myself?

Thanks for the help!

---

### Post by buddhaflow on 2013-02-06
It's a bit of a hack, but install imageinfo, then type:

imageinfo --iccname test.jpg

It will squak if no LCMS.

I think you have to build from source if you want it :(

---

