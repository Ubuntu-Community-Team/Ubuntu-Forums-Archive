---
title: "Cheese locks up computer"
date: 2012-05-07
forum: General Help
---

### Post by Derek Karpinski on 2012-05-07
My webcam works in Skype, it also works when installing Ubuntu, and they ask to take my picture.

Cheese worked great in 10.10, but hasn't since.  If I run cheese, it runs the CPU 100%, and eats up all my memory, starts swapping, and I play hell trying to get to a terminal or tty to kill it.

Does anybody have any ideas on how to fix or trouble shoot this?

Oh, ubuntu 12.04 64 bit.

---

### Post by guestolo on 2012-05-08
Is this using CPU extremely as you open Cheese?  
Or after you take a photo or start Video?

---

### Post by robert shearer on 2012-05-08
you could try guvcview and see if that has the same problem.
```
sudo apt-get install guvcview
```

which would help in determining if it is Cheese or a webcam solution thats needed.

guvcview seems to work on a number of machines that are too resource light for cheese.

---

### Post by Derek Karpinski on 2012-05-08
> **guestolo said:**
> Is this using CPU extremely as you open Cheese?  
Or after you take a photo or start Video?

As soon as I start cheese the CPU usage ramps up, and the memory is eaten.  I never even see the GUI for cheese.

> **robert shearer said:**
> you could try guvcview and see if that has the same problem.
```
sudo apt-get install guvcview
```which would help in determining if it is Cheese or a webcam solution thats needed.

guvcview seems to work on a number of machines that are too resource light for cheese.

I'll try it, but cheese worked great with this webcam and computer in 10.10.  It also works great in Skype.  It is a cheap cam though.

---

### Post by Derek Karpinski on 2012-05-09
> **robert shearer said:**
> you could try guvcview and see if that has the same problem.
```
sudo apt-get install guvcview
```which would help in determining if it is Cheese or a webcam solution thats needed.

guvcview seems to work on a number of machines that are too resource light for cheese.


guvcview works perfectly.

---

### Post by Derek Karpinski on 2012-05-09
In fact, I'm so happy with guvucview that I don't care to install cheese anymore.

---

### Post by robert shearer on 2012-05-09
> **Derek Karpinski said:**
> In fact, I'm so happy with guvcview that I don't care to install cheese anymore.

Agreed.. :)  
Some systems work well with cheese and on others, mine include, cheese is a little stinky.

Sometimes cheese can be real stinky. 

guvcview is a fine alternative and the control options do allow the fine tuning that some webcams require to perform at their best.

---

