---
title: "moving files between partitions"
date: 2011-01-14
forum: General Help
---

### Post by .hettinger on 2011-01-14
Hi, I appreciate all the help.  I am going to get to the point, I have windows 7 and am soon to partition a large amount of my drive over to linux.  I'd rather all of my computer be linux but I'm unsure how to get my files to my other partition, I don't have a thumbdrive and my email doesn't have much space.  I have 300 gbs of room, 150 will be linux, how do I get the 100 gigs moved from my windows partition to my linux so I have more space on my linux.

---

### Post by 3Miro on 2011-01-14
First of all, this sounds like a bad idea. Messing with partitions can always lead to losing data (double so if you are not 100% sure what you are doing). If you are going to change the partitions BACKUP EVERYTHING IMPORTANT. Burn CD/DVDs or get an external HDD. I know it is an expense and a hassle, but better safe then sorry.

Having said that. You should be able to boot from a liveCD and then select "Try Ubuntu" (don't install). Then from System -> Admin -> Gparted, you can move/resize partitions on your HDD. You can also "mount" both your Windows and Linux partitions and move files around (go to places -> Home and you should see the partitions on the left). You can mount the windows partition from Linux without the liveCD (i.e. just boot normally), but you cannot change the Linux partitions.

---

