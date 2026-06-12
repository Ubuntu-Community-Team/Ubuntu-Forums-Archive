---
title: "could this be right?"
date: 2011-03-10
forum: General Help
---

### Post by m91-30 on 2011-03-10
I installed ubuntu 10.10 64 bit, and let it partition the drive how it wanted. it partitioned out 10.6 GB from the drive's total space and shared it with swap AND root. is this right?

I've been having issues with my computer refusing to come out of sleep, and it takes 10 minutes or so to go into, and come out of hibernate.

could these two things be related?

---

### Post by slooksterpsv on 2011-03-10
> **m91-30 said:**
> I installed ubuntu 10.10 64 bit, and let it partition the drive how it wanted. it partitioned out 10.6 GB from the drive's total space and shared it with swap AND root. is this right?

I've been having issues with my computer refusing to come out of sleep, and it takes 10 minutes or so to go into, and come out of hibernate.

could these two things be related?

Yeah Ubuntu doesn't take a whole lot, it's more of the user data that takes up the most (your documents, music, pictures, videos, etc.).
Hibernate requires, IIRC, double the amount of RAM you have to hibernate. Hibernate takes a long time on mine as well.
As for coming out of sleep, do you get your mouse cursor? Or can you have your mouse? Also what are the specs of your computer?

---

### Post by m91-30 on 2011-03-10
is it right that they are sharing the same partition, though?

it's a toshiba sattelite A305D with an AMD turion x2 rm70 at 2ghz and ATI radeon 3100, and 4 gb of ddr2 800MHz RAM.

---

### Post by searchfgold6789 on 2011-03-10
To answer your initial question: Linux distributions such as Ubuntu often take advantage of a handy little thing called an Extended Partition, which itself can contain a few smaller regular partitions inside of it. This way you can have more partitions on one disk. So I would not be surprised if your Swap and root partitions are in the same extended partition - In fact that is how my Xubuntu system happens to be set up and is probably the default as of now.
The way your disk is partitioned probably does not have much to do with your current problem which is getting it to come out of Sleep. I do not know a surefire way to solve this but I would just disable sleep mode :)
 - search

---

### Post by m91-30 on 2011-03-18
thanks for your replies. I guess my computer just doesn't like linux sleep mode.

---

### Post by 5149.5 on 2011-03-18
It sounds like you are running on a swapfile. It is usually in /var though so I'm not sure. Check this link. I just went through the process of creating a swap partition and shutting down the swapfile. See this link.

[http://manpages.ubuntu.com/manpages/hardy/man8/dphys-swapfile.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/dphys-swapfile.8.html)

---

