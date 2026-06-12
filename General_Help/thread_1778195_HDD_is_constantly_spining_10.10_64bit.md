---
title: "HDD is constantly spining 10.10 64bit"
date: 2011-06-08
forum: General Help
---

### Post by Gh0zt36 on 2011-06-08
and it gets the hdd very warm and keeps the fan on constantly as well generally heating the whole system . was so bad i ended up having to go back to windows anything i can do to get the hdd to go in standy by when in active like windows ???? cause i hate windows and love ubuntu but i dont wanna burn up my machine to keep ubuntu

---

### Post by Gh0zt36 on 2011-06-10
Bump for answer?

---

### Post by pqwoerituytrueiwoq on 2011-06-10
care to tell us your hardware?
system->preferences->power management
you will see a option that will catch your eye

---

### Post by Gh0zt36 on 2011-06-10
> **pqwoerituytrueiwoq said:**
> care to tell us your hardware?
system->preferences->power management
you will see a option that will catch your eye

oh sorry hardware is t3400 pentium dual core 2.16 ghz with 4 gb ram and a 250 western digital EXternal and vista is on a 500gb western digital hdd
well ill check that out right now thank you sir

---

### Post by Gh0zt36 on 2011-06-11
clicked spin dow hd when possible no change. its still constantly spinning i can feel it in my hand and i d//l toshutils but i dont know any of the commands for it and cant find any on google

---

### Post by pqwoerituytrueiwoq on 2011-06-11
since you have 2 hard drives i assume this is a desktop
```
sudo hwinfo --short > ~/Desktop/hwinfo.txt
```
run that command there will be a file on your desktop with specifics in it on your hardware

---

### Post by Gh0zt36 on 2011-06-11
its actually not sorry i put hd for both accidently but 250 is ext  ... i have a 500gb hd in the lappy and 250gb on external but i switched for a while cause i wanted linux full time but the hd wouldnt stop spinning and the fan was always on  i got the 250 as ext right now

---

### Post by pqwoerituytrueiwoq on 2011-06-11
the terminal program powertop (needs sudo)
it can tell you what is writing/reading from your hdd thus keeping it spinning
[[IMG]http://i52.tinypic.com/6o1m3q_th.png[/IMG]](http://i52.tinypic.com/6o1m3q.png)
idea how much ram do you have to spare? (is thinking of making /tmp into a ram disk)
i think it does not know the difference between reading/writing

---

