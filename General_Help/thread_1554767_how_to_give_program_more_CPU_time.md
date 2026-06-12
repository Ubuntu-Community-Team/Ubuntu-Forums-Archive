---
title: "how to give program more CPU time?"
date: 2010-08-17
forum: General Help
---

### Post by TygerTung on 2010-08-17
I downloaded flightgear and even though my computer is pretty powerful (P4 3.2 GHZ 1.5 gig of ram and a ati radeon 9600 pro graphics card) it runs pretty slow.

I did notice that there were no proprietry drivers in use on the system, does this mean my graphics card has no real 3d driver in use?

When using flight gear the cpu seemed only to be about 30-40 percent in use! How can I get it to go 100% in use to make the game run much better?

---

### Post by TNT1 on 2010-08-17
You can right click on a process in system monitor to change its priority.

---

### Post by TygerTung on 2010-08-17
I did that and it had a lot of priority but the cpu was only still doing 44 percent while on full screen I was getting 3 frames per second and on windowed I was getting a whopping 6.

This really isn't ideal and there must be some way to fix it.

---

### Post by deathadder on 2010-08-17
I'm not sure how the system monitor works, or what level of control it'll provide. But from the command line you can you the [nice, or renice, commands]("http://www.linux.com/archive/feed/58638"). They may provide more control than the system montior...

---

### Post by TygerTung on 2010-08-17
It appeared to be doing some magic with regards to nice and I had a system box up and everything, but all to no avail!

---

### Post by mastablasta on 2010-08-17
I don't have experience with this one in Linux, however in windows (with ATI) i experinced same issues. Tunning down various effects could help. However to me result was the same. Despite having stronger graphics card than you do.
 
Solution was bizzare. I turned on the logs. Well actually the guys at flighgear told me to do that in order to do diagnostics. But as soon as i turned the logs on graphics ran much faster and are now working normally (almost full effects on). 
 
I then slowly reduced the number ofl logs and noticed that even small logging had improved permformance as a result. i call thi sweird.
 
Try it. it might be the same thing in Linux.
 
EDIT: if it still doesn't work ok i suggest to visit flightgear forums. people are very friendly there. ;-)

---

### Post by TygerTung on 2010-08-17
Oh yeah, how do I get these logs whizzing along?

Turning off effects didn't really have any effect.

It runs even slower in windows as well I believe.

---

### Post by philinux on 2010-08-17
> **TygerTung said:**
> I downloaded flightgear and even though my computer is pretty powerful (P4 3.2 GHZ 1.5 gig of ram and a ati radeon 9600 pro graphics card) it runs pretty slow.

I did notice that there were no proprietry drivers in use on the system, does this mean my graphics card has no real 3d driver in use?

When using flight gear the cpu seemed only to be about 30-40 percent in use! How can I get it to go 100% in use to make the game run much better?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

