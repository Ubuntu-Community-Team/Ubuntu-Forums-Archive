---
title: "trouble playing dvds"
date: 2010-09-17
forum: General Help
---

### Post by tomj528 on 2010-09-17
I'm still having trouble playing DVDs.  I've downloaded all of the codecs and software.  When I try to play a dvd in mythtv I get a blank blue screen for about 5 seconds and then it returns back to the menu.  I figured that the frontend couldn't find the dvd drive and I looked in /dev and saw that the dvd drive was /dev/dvd1.  I then changed the frontend setting to /dev/dvd1 and the dvd then started to play.  After 10 seconds I got kicked out with a frame buffer error.  I rebooted and tried to play the dvd again and I got the original blank blue screen. going back to the menu.  I checked the frontend settings and they were still /dev/dvd1.  When I checked the /dev folder the dvd drive was now /dev/dvd2.

Any Ideas how to keep the computer from renaming the dvd drive?

---

### Post by uRock on 2010-09-17
Have you added the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

---

