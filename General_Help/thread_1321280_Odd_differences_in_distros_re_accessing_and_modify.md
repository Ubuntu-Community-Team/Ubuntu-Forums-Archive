---
title: "Odd differences in distros re: accessing and modifying partitions/drives"
date: 2009-11-09
forum: General Help
---

### Post by ozguitarplayer on 2009-11-09
Hi, 
More a general question rather than a problem to solve...

I have installed a number of times the following; Hardy Heron, Jauntu Jackalope, Karmic Koala and Debian Lenny.

I have noticed that with, Karmic Koala and Lenny that in order to access and modify other partitions and drives I must first make a directory for each partition/drive, edit /etc/fstab to suit and chmod and chown.

Yet with Hardy Heron and Jaunty Jackalope I can access and modify the other partitions/drives automatically and when I look there is no entry in /fstab nor do I need to chmod or chown.

Has anyone else found the same thing? 
Is there a reason for this?

---

### Post by ranch hand on 2009-11-09
I have had no difference in accessing other drives with Nautilus form Hardy (where I came in) on.

I can say that there is no difference in kernel 2.6.32 as of yet either (early 10.04 testing, yes I am nuts).

---

### Post by ozguitarplayer on 2009-11-10
Yes it all works well with Hardy.
Are you saying that since 2.6.32 there haven't been any changes in the kernel so the different distros should work the same?
Nigel

---

### Post by ranch hand on 2009-11-10
Nope, I am saying that I have had the same performance in all my distros since Hardy.  2.6.32 is brand new, 9.10 runs 2.6.31.

I have never done a thing to my fstab file to cause this and they all look, or looked, about the same.

I would about bet that your problem is thee interaction of the version interaction with your bios in some way.

---

### Post by ozguitarplayer on 2009-11-10
thanks ranch hand, I hadn't concidered the BIOS, any clues as to where to look or does it depend to much on the make of the motherboard?

---

### Post by ranch hand on 2009-11-10
Bios is the firmware of your Mother Board.  You are probably doomed to this on again off again performance if that is the problem.

I really hope that I am wrong.

---

### Post by ozguitarplayer on 2009-11-10
well at least I'm learning a lot about it so that's good I was curious as to why more than anything else, if in time Isort it I'll post again, thanks ranch hand

---

### Post by ranch hand on 2009-11-10
That is one thing, there is always something to learn.  I usually learn by breaking things, but then again I am clumsy.

---

### Post by ozguitarplayer on 2009-11-10
that's why I've done a lot of installs since this time last year when I started using Linux my curiosity ends up damaging things..

---

### Post by ranch hand on 2009-11-10
> **ozguitarplayer said:**
> that's why I've done a lot of installs since this time last year when I started using Linux my curiosity ends up damaging things..
I am getting better at fixing the buggers.  Playing with the "testing" release helped a lot with that.

Not that I recommend that.  I wouldn't do it on the same drive with my "main" OS and some say the same box is a mistake.  I just turned off my "main" drive in bios and hoped the bugger wouldn't kill any hardware.  It didn't.

---

### Post by ozguitarplayer on 2009-11-10
I ended up getting a 2nd computer to act as crash dummy, this was a huge relief, before that I had one HDD with 3 o/s and with another partition for all my working files.

---

### Post by ranch hand on 2009-11-10
> **ozguitarplayer said:**
> i ended up getting a 2nd computer to act as crash dummy, this was a huge relief, before that i had one hdd with 3 o/s and with another partition for all my working files.
+496

---

