---
title: "installing from disc no dual boot"
date: 2011-05-22
forum: General Help
---

### Post by soulcat on 2011-05-22
hi
 
while installing ubuntu 10.10 from disc on a free partition i'm only getting 2 options instead of 3 'use entire disk' & 'advanced install' but no installing along side other operating system
i really want to install along windows 7 as a dual boot, but how do i do this is the option is not there
i'v had a look at advanced but looks a bit daunting.
 
regards

---

### Post by coldraven on 2011-05-22
You could try this..
Boot from the Live CD, select "Try Ubuntu"
Run System>Admin>Gparted
Find the partition that you would like to install to and delete it. It will then show as "Unallocated". Make sure you select the correct one! Nothing permanent will happen until you select "Apply" at the top of the screen.
Re-boot with the Live CD.
Then try to install, you should see the"Install Alongside" option.

---

### Post by sikander3786 on 2011-05-22
There has been a problem with that option in Maverick. Hope this link would help you understand all that stuff.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

---

### Post by soulcat on 2011-05-22
thanx 

coldraven that worked a treat

thanx for all the replies

---

