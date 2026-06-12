---
title: "Burning ISO Image in Brasero"
date: 2009-12-13
forum: General Help
---

### Post by carolina on 2009-12-13
This is my first attempt at burning an iso to a disc so i am not sure what to expect as far as time needed to burn the actual image after the check sum notice .

Estimated time remaining shows as 6 min 39 sec but just keeps going up and has been burning for maybe an hr already . Is this normal ? And any time frame reference appreciated as i just don't want to set here all day if it's not normal .  :popcorn:

I set burn at lowest possible speed ( 16 ) and using Brasero within Ububtu 9.04 for 9.10 iso 386 image .


Insight Appreciated

---

### Post by jmszr on 2009-12-13
carolina,

No, that is not normal. I suggest using k3b to burn your .iso:

```
sudo apt-get install k3b
```

I've not had a problem with it.

---

### Post by carolina on 2009-12-13
> **jmszr said:**
> carolina,

No, that is not normal. I suggest using k3b to burn your .iso:

```
sudo apt-get install k3b
```I've not had a problem with it.


Thanks for that tip . I will see if i can get that installed and try it for the burn . I assume the burn process will be essentially the same in k3b ?

---

### Post by jmszr on 2009-12-13
carolina,

Once k3b is installed (and opened) just click on "Burn CD Image" and then find your .iso file under "Image to Burn", set speed, and then "Start" and you should be good to go.

---

### Post by carolina on 2009-12-14
> **jmszr said:**
> carolina,

Once k3b is installed (and opened) just click on "Burn CD Image" and then find your .iso file under "Image to Burn", set speed, and then "Start" and you should be good to go.


Wow , thanks guy . Installed , ran and burned disc in 6 min . I am very impressed with this program .


PS - Noticed you are in Phoenix area and i  have a friend there - Tom Shorb . Know it's a long shot but wonder if you happen to know him ?

---

### Post by jmszr on 2009-12-14
carolina,

No, I haven't had the pleasure of meeting Tom Shorb; it's kind of a big city. I'll remember the name, though, in case I do run across him.

Glad k3b did you right.

---

### Post by scouser73 on 2009-12-14
Yeah, that's definitely not normal, especially for Brasero.  Install K3B as instructed and see if you can successfully burn the ISO.

---

