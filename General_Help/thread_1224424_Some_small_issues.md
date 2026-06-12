---
title: "Some small issues"
date: 2009-07-27
forum: General Help
---

### Post by Jimstehrman on 2009-07-27
hello

I have had some experience with Ubuntu in the past, and recently decided to try it out again with the release of Jaunty. I have it installed on an Acer Aspire 8930, 64 bit. I installed it from Vista with Wubi, and everything worked fine after a few tweaks. Recently It may have had something to do with a set of updates, Jaunty will freeze, theres no response from any input and the caps lock key blinks. 

Also Jaunty never wants to shut down or restart my computer, it will just go to a blank screen and hold it. 

Lastly and least importantly, rythmbox often does not want to see my music collection which is on a partition. I can access it from places, but occaisionally it will refuse to admit it exists, I've tried various other players and I think Exaile has been the most tolerant of this.

Any help would be awesome, 
thanks guys

---

### Post by t4thfavor on 2009-07-27
I had the same issue on my Toshiba, I think that means its having a kernel panic. I have since updated the OS a few times, and the problems have dissapeared. Try taking a look at the system logs, and look for panic's.

The other issue, I believe is caused by the "partition" not being mounted when you run the player. Try accessing it one time through places, and then opening the player. Then reboot, and just open the player. I bet the latter will refuse to show the music.

---

### Post by Jimstehrman on 2009-07-27
thanks a bunch, It was that the drive wasn't mounted, there isn't a way to auto mount it, or make it always accessible?

---

### Post by Vaphell on 2009-07-27
you can do that permanently by editing /etc/fstab

look up for precise instructions, there should be a lot of threads covering that topic

---

