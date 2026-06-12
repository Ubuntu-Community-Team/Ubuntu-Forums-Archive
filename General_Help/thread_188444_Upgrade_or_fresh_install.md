---
title: "Upgrade or fresh install?"
date: 2006-06-04
forum: General Help
---

### Post by torx on 2006-06-04
I'm relatively new to Linux and my limited knowledge tells me that it wouldn't make a difference if i upgrade to Dapper Drake or did a fresh install. 

Am i wrong?

---

### Post by adam.tropics on 2006-06-04
Many here prefer to fresh install, for a host of reasons from testing to clearing the decks, so to speak. Personally I prefer to upgrade as for me it's a whole lot less hassle,,,
So sort out your sources list, then

sudo apt-get update
sudo apt-get dist-upgrade

the result should be the same.

---

### Post by daschl on 2006-06-04
well i think the best solution is maybe:

- try an update first (because it is not so time-consuming and your personal data isnt lost [btw: it is always a good idea to put your /home und an other partition])

- if the update fails, you obviously have to do a fresh install

(that's what i do, maybe it works out for you too)

---

### Post by Zerocool10482 on 2006-06-04
This is the process I did that worked for me.

1. Burn the Install and Live cd.
2. Back up your /home to a cd.
3. Try to update with the update manager.
4. Then if it didn't work. Use the live cd to back up anything else or just to get to the internet.
5. Use the install cd if everything fails.

---

