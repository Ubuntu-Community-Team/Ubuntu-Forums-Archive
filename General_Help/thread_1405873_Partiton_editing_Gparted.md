---
title: "Partiton editing Gparted"
date: 2010-02-13
forum: General Help
---

### Post by Sale 666 on 2010-02-13
Hey i have a problem... my 500GB drive died on me =(... that was my windows 7 game dirve and ubuntu drive too (dual boot) my other 200GB is still alive :).. (well no harm done had win on it XD)...

So here is my problem i replaced the 500GB drive now with an IDE 80 GB drive since i dont have others ATM. And installed ubuntu on the 80 GB drive 
wile the 200 gb drive contains back up data i dont want to mess with it!

I downloaded Gparted trough synaptic and i know how to work with it the problem is i cannot resize my 80gb partition (all ubuntu)... 
id like to resize it 50-50 is it possible wile system is running?
cause it is greyed out!

So the thing would be 40gb windows 7, 40 GB Ubuntu
and the 200GB drive i would be installing games there i use 7 for gaming since wine and cedega are not so perfect good but not perfect ;) :popcorn:

Thanks!

---

### Post by Ghost|BTFH on 2010-02-13
It's not possible because you most likely told it to use the whole disk instead of making / /swap and /home partitions like a good linux geek.

This presents you with the unique problem of not being allowed to resize or modify a mounted partition (which the whole drive is currently or you wouldn't be able to see gparted) which means it's just not going to happen.

The good news is, Ubuntu is quick and easy to install so, go have at it again, and this time actually edit the partitions the way you want before you install.  My suggestion would be:

/ = 9gb
swap = 1gb
/home = 30gb
FAT32 = 40gb

Set that up properly and you'll be good to go.

Cheers,
Ghost|BTFH

---

### Post by Grenage on 2010-02-13
Or you can run gparted from the live CD, then the filesystem won't be mounted and you can resize it.

---

### Post by Ghost|BTFH on 2010-02-13
> **Grenage said:**
> Or you can run gparted from the live CD, then the filesystem won't be mounted and you can resize it.

^ o_O  See what happens when you're all awake and stuff?  Smart thinkin'.

---

### Post by Sale 666 on 2010-02-14
DUUUHHHH now i feel retarded XD
"Or you can run gparted from the live CD, then the filesystem won't be mounted and you can resize it."... dang why dont i use this penaut i call brain XD?

---

### Post by Grenage on 2010-02-15
Hindsight is always 20/20. :)

---

