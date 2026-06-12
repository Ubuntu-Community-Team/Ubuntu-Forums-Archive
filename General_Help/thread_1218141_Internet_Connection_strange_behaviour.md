---
title: "Internet Connection strange behaviour"
date: 2009-07-20
forum: General Help
---

### Post by yasirhussain on 2009-07-20
Hi All! I am a relatively new user of ubuntu (using for 6 months). 
I have a dual boot of ubuntu along with win xp and use a wimax connection. every thing was working fine till a week ago. but then my internet connection started behaving strangely. when i start ubuntu, the lan connection is present, driver working (r8169) but firefox or any other application is unable to access internet..
a more strange thing is that when i logout from my user and login to root user, it starts working.:confused: wether i use root or again login to any other user.:P i dont know what is happening. win xp is working fine. pls help me:(

---

### Post by fragos on 2009-07-20
It almost sounds as if a binary or script envolved in starting up an Internet connection doesn't have execute permision for the user. Most executables belong to root but allow the user to execute. If you've done any manual configuration editing that would be a file look at for the correct permissions, Others Read and Execute.

---

