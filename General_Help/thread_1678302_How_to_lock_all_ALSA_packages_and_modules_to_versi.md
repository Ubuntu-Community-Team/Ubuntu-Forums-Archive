---
title: "How to lock all ALSA packages and modules to version 1.0.23"
date: 2011-01-30
forum: General Help
---

### Post by mastablasta on 2011-01-30
I am using 10.04 but i need alsa to be upgraded to 1.0.23 in order for the sound to work.

every once in a while when there is a system update alsa gets overwritten and goes back to 1.0.22 which makes the computer unusable. 

i already locked the alsa packages and it worked now for some time.

but today i got another update that did the same thing. the only solution is to do full alsa upragade again. is there really no other way?

which packages do i need to lock to keep alsa at 1.0.23?

i don't want to move to 10.10 as i planned to stay with LTS. but if there is no other way...

funny how debian chose to use 1.0.23 for their next stable edition, while ubuntu LTS stays with 1.0.22 despite it not working on many newer cards. especiall intel ones it seems.

---

### Post by mastablasta on 2011-02-02
BUMP.
 
Does adding a PPA for alsa 1.0.23 solve this issue?

---

### Post by Larrxi on 2011-02-02
Try this: [https://help.ubuntu.com/community/PinningHowto#Introduction to Holding Packages](https://help.ubuntu.com/community/PinningHowto#Introduction to Holding Packages)

---

### Post by mastablasta on 2011-02-03
you missunderstood. The ALSA packages are locked (my bro locked them for me) but the kernel updates and also it seems some other manage to break the packages.
 
My questions is: would adding ALSA PPA solve my issue or do i need to go through upgrade (stopping drivers, removing them, building, installing, configuring) everytime there is a bigger upgrade?
 
Or does anyone know which packages exactly should be locked? perhaps my bro didn't  lock them all, though i think he was preety thorough.
 
I am not sure how the locked packages get overwritten but those updates do make a mess of the system. it even causes some programes to crash (such as skype).
 
if the problem continues i will be forced to update to 10.10, but otherwise i was planning to stay with 10.04. I am sure i am not the only one with this problem but i don't know the search terms to find any good info on this in google.

---

### Post by mastablasta on 2011-02-09
bump

---

### Post by dino99 on 2011-02-09
there is no serious reason to stay on 10.04

---

### Post by mastablasta on 2011-02-15
you are actually correct, but 
 
long term support, stability.... i wanted them. and the thing is everything else seems to be working just fine.
also upon upgrade i need to do all the setting up again of mail accounts etc. 
 
or maybe i should switch to Debian 6 (stable) that has the latest ALSA?!

---

