---
title: "Grabbing update from karmic repos"
date: 2009-09-30
forum: General Help
---

### Post by kachofool on 2009-09-30
Hey all... I'm running 9.04, but I want to grab an updated version of a package without compiling myself. I'm looking for qt-creator (1.1) but the 9.04 package is 1.0. 

The karmic koala repo has 1.1... could I still get that package some how? (Like maybe adding the karmic repos somehow?)


Regards,

-KF

---

### Post by akakingess on 2009-09-30
I really don't have an answer for you, but have you tried just doing something like
```
sudo aptitude qt-creator update
```
and see if that will manually update it? That's the only input I would know to try. I do have one machine running 9.10 and have had very minimal problems, have you thought about installing 9.10?

---

### Post by kachofool on 2009-09-30
no go =(

---

### Post by akakingess on 2009-09-30
Sorry I don't have any other suggestions, it probably would be the safest thing anyways, because of libs and whatever other dependencies it may have that could mess up other stuff within Jaunty, I guess your best bet is to upgrade to Karma, unless someone more knowledgeable chimes in soon.

---

### Post by kachofool on 2009-09-30
I thought I'd post this up for future reference... 

I'm on 9.04 and installed the latest developer qt packages available through the 9.04 repos (I have *not* installed qt-creator)

The latest qt-creator is available here:
[http://qt.nokia.com/downloads](http://qt.nokia.com/downloads)

The download is a *.bin file. Download the file somewhere and use chmod to make the file executable.

Then run it from the folder you downloaded the file to ./qt...etc

The installer will guide you through the rest.

---

### Post by akakingess on 2009-09-30
Glad you got a resolution, sorry I wasn't any help, but is it working just fine under 9.04?

---

