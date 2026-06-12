---
title: "Astronomy software for distance calculation"
date: 2009-07-14
forum: General Help
---

### Post by tavi_10 on 2009-07-14
Hi!

I am looking for an astronomy software that calculates distance between any 2 planets from our solar system (asteroids would be also nice to have) (the distance should be in km or miles). Is there anything like this available for Ubuntu?

As i have a lot of calculation to do (about 3.3 mil), a command line interface would be extremly useful (i'll use a php script to do all the calculations).

I saw something interesting in astrolog, but unfortunatelly, it gives the angular distance instead of what i am looking for. I could use from this the generalization of Pythagorean theorem, aproxmating the orbits to circle and knowing the distance between the Sun and each planets orbit, but i am looking for something more precise.

Thank you for your time,
Octavian

---

### Post by Freezing on 2009-07-14
try Kstars you can download it and install it thought add/remove programs.
Its just a litlle comlicated am still trying to found out how to calculate distance if you do please let know.
:)

---

### Post by tavi_10 on 2009-07-14
Thank you very much for the info!

Take a look at [http://docs.kde.org/development/en/kdeedu/kstars/tool-calculator.html#calc-planetcoords](http://docs.kde.org/development/en/kdeedu/kstars/tool-calculator.html#calc-planetcoords) . That tool will do the trick. 

For my calculations i'll just automatically create a batch file with all the data i need and that should be it. Still a little uncertain for the moment on how exactly i'll do the math (i see some distance to Earth, distance to Sun, but not interplanetary distance), but some simple 2D geometry should be enough (assuming that the body is on the ecliptic plane, but that is not the case for Pluton and some other bodies).

---

### Post by NIKE. on 2009-07-14
Admittedly I don't know much about astronomy, but why would the distances be measured in miles or km? Would they not be LY (to measure stars) or AU (astronomical units) to measure the distance between the planets?

---

### Post by tavi_10 on 2009-07-14
It makes no difference. I just wanted to point out that i don't need the angular distance that some software/ephemeries provide. Kstar provides the data in AU, but it doesn't bother me.

---

