---
title: "It wont let me increase partition..."
date: 2009-11-28
forum: General Help
---

### Post by DarkSunrize on 2009-11-28
Ok im booted from my live CD on ubuntu 9.04. Im creating a lager partition for ubuntu. But it wont let me make it larger. I shrunk my old windows partition. I have 28.46 gigs unallocated space but when i click on ext3 in GParted it will only let me shrink the partition. What do i do??
 
(do i have to shrink it a little b4 i can increase it?)

---

### Post by DarkSunrize on 2009-11-28
can someone please help me!!! I rly need to increase the partition size!!

---

### Post by DarkSunrize on 2009-11-28
ok rly someone PLEASE HELP!!!!!!!

---

### Post by audiomick on 2009-11-28
I can only assume that the partitioner is already set to make the total available space into an ext 3 partition. The partitioner is fairly fool proof.

Can you post a picture of what the partitioner screen looks like?

---

### Post by whoop on 2009-11-28
Maybe you didn't increase the extended file system first? 
As audiomick said, a screenshot or more detailed information will help...

---

### Post by fluffman86 on 2009-11-28
Whoa, there, Cowboy!  Calm down.  Give people a little more than 5 minutes to respond.  We're not a dedicated staff of your personal Tech Support.  You can check out IRC sometime if you want a more "live" feel.

Anyway, do what whoop said.  Look for a blue line around your ext3 partition.  edit that extended/logical partition first, and make it bigger, THEN make your ext3 partition bigger.

---

### Post by DarkSunrize on 2009-11-28
haha srry fluff i was just asking a question i didnt know u were gonna go to my thread... im just desperately trying to get this to work... i increased the ext3 partition but it also multiplies all of the files i had in there so the whole thing is still taken up?? o.0 idk how that happened... so do u think i shuld re-install?

---

### Post by Iron Calves on 2009-11-28
Have you downloaded a lot of stuff on your hard drive and nearly maxed it out? I had the same problem trying to get Ubuntu on mine. 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

This is how i fixed mine, if you're having the same problem.

---

### Post by T.R. on 2009-11-28
You'll have to shrink the other partition before you can increase the Ubuntu one.

---

### Post by DarkSunrize on 2009-11-28
> **Iron Calves said:**
> Have you downloaded a lot of stuff on your hard drive and nearly maxed it out? I had the same problem trying to get Ubuntu on mine. 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

This is how i fixed mine, if you're having the same problem.


no my hard drive has like 200 gigs of space still free

---

### Post by Iron Calves on 2009-11-28
> **DarkSunrize said:**
> no my hard drive has like 200 gigs of space still free

Mine had a good bit of free space as well. For some reason it wouldn't let me downsize it. I have some windows system file at the end of the hard drive it wouldn't let me go past even though I had all that free space.

---

### Post by DarkSunrize on 2009-11-28
> **Iron Calves said:**
> Mine had a good bit of free space as well. For some reason it wouldn't let me downsize it. I have some windows system file at the end of the hard drive it wouldn't let me go past even though I had all that free space.


Well i got it to work but i got an error in the middle of it soo now im gonna just re-install i guess..

---

### Post by ed-koala on 2009-11-28
I read another post recently about this issue.  Windows has non-movable stuff making partitioning a nightmare.  he answer was going into Windows, deleting all the system restore points except the most recent, running defrag, and then shrinking the windows partition using windows tools.  THEN do the resize of the ubuntu stuff.

---

