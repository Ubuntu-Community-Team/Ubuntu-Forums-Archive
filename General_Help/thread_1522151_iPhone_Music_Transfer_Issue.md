---
title: "iPhone Music Transfer Issue"
date: 2010-07-01
forum: General Help
---

### Post by tekkidd on 2010-07-01
Hi i am running ubuntu 10.04 with an iPhone 3G 4.0 Jailbroken. My issue is that when i try to transfer songs to it in rhythmbox, it transfers the song (it shows on the up on the list of songs that is on the iPhone) but when i go to the iPod app in the iPhone the song(s) do not show up. However when i go and plug it into a mac or a pc and fire up itunes the song only after that shows up on the ipod app in the iPhone. 

PS: I am running libimobiledevice v. 1.01

---

### Post by elsettler on 2010-07-04
I'm having the same issue right here... did u find a solution to it in these 2 days?

---

### Post by Rob Edwards on 2010-07-07
Got the same - any solution?

---

### Post by tekkidd on 2010-08-14
Solution Found:

GO TO: /home/<username>/.gconf/rhythmbox/state/ipod

AND DELETE: %gconf.xml

then restart rhythmbox

---

