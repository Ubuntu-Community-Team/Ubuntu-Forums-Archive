---
title: "multiple issues! please help!"
date: 2009-12-03
forum: General Help
---

### Post by steve19137 on 2009-12-03
i put this in the general help section because i have a wide range of issues, from space to needed tutorials. so the immediate issue that i have run into right now is with virtualbox.

[CENTER]**Next Section is SOLVED!!!!!**
[/CENTER]

i previously have win vista, and because i bring this laptop to school, i need to have some degree of familiarity and "sameness" as the rest of my class. so i made a new vm, installed windows, and discovered that my home folder is full, and windows is unable to boot for the first time based on the fact. so is there a way to increase my home folder to the whole hard drive? my brother and sister also have accounts on this computer, so it may be a contributing issue. that is the issue i have right now. 

[CENTER]Not Solved Yet
[/CENTER]

second is about WINE. i own a bunch of star wars pc games, and i have read that you can play WoW on ubuntu with wine. so is there a different procedure because of different publishers? the games i want to install are the games from the "Star Wars: Best of PC" package, and LEGO Star Wars I and II.

[CENTER]Not Solved Yet
[/CENTER]

another thing about wine. how can i install itunes with it? i use the new home sharing feature often, so this is a pressing issue.

[CENTER]Not Solved Yet

[LEFT]i have a spare 120GB hard drive, and i want to migrate my system over to it. i can connect via USB, but i dont think a simple copy and paste will do it. is there a way to, in a sense, clone my hard drive?
[/LEFT]
[/CENTER]
 
but what i dont need help with is removing passwords from my brother and sisters accounts, i figured that out from another thread on the forum, and i dont need help with silverlight/moonlight. so if there are tutorials that can be linked, please do so. i have searched extensively for the answers to these issues, and if i have others i will update this thread. thanks :)

---

### Post by mörgæs on 2009-12-03
You can not increase the size of /home, but with Gparted you can increase the size of the partition, on which /home is. Don't forget back-ups before doing so.

There is a good tutorial in the sticky threads in Absolute Beginner Talk.

---

### Post by steve19137 on 2009-12-03
> **mörgæs said:**
> You can not increase the size of /home, but with Gparted you can increase the size of the partition, on which /home is. Don't forget back-ups before doing so.

There is a good tutorial in the sticky threads in Absolute Beginner Talk.

thank you sooo much!!! that is a life saver. so i will edit my first post to say that that is solved.

---

### Post by oldos2er on 2009-12-03
You can check Wine's database of Win* apps here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

 I don't think iTunes will run in Wine, but since I don't "do" iTunes, I don't know for sure.

---

### Post by steve19137 on 2009-12-03
> **oldos2er said:**
> You can check Wine's database of Win* apps here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

 I don't think iTunes will run in Wine, but since I don't "do" iTunes, I don't know for sure.

thanks for the link, but it gives me bad news. itunes 9.0.2 doesnt work. oh well. i can still listen to pandora. oh, btw, is there a pandora app for linux?

---

### Post by steve19137 on 2009-12-03
> **mörgæs said:**
> You can not increase the size of /home, but with Gparted you can increase the size of the partition, on which /home is. Don't forget back-ups before doing so.

There is a good tutorial in the sticky threads in Absolute Beginner Talk.

actually, i discovered this myself, but the only way to do that (without costing me sleep) is to boot from my live cd, and unmount the HD that way, and change the partition sizes better. but now i have a question. when i installed (i installed on 8.whatever (i cant remember)), it asked if i want swap space. and i have it 5gbs, not knowing what it was. now i think that the "swap space" is the home partition. am i right? if not, what is that swap space, and where is it?

---

### Post by SeattleOtaku on 2009-12-03
I'm not familiar with the newer "Home Sharing" part, as it seems to require a iTunes Store account login, etc.  But there are some like Songbird ([http://www.getsongbird.com/](http://www.getsongbird.com/)) that can setup a "watch" directory to auto-import to its library as files are saved/updated in the watched location.

For Pandora, try at [http://linuxappfinder.com/package/pandora-radio](http://linuxappfinder.com/package/pandora-radio) perhaps.  :)

---

### Post by mörgæs on 2009-12-03
> **steve19137 said:**
> actually, i discovered this myself, but the only way to do that (without costing me sleep) is to boot from my live cd, and unmount the HD that way, and change the partition sizes better. but now i have a question. when i installed (i installed on 8.whatever (i cant remember)), it asked if i want swap space. and i have it 5gbs, not knowing what it was. now i think that the "swap space" is the home partition. am i right? if not, what is that swap space, and where is it?

If you run ```
sudo fdisk -l
``` you will see the sizes of your partitions. Most likely one is marked 'swap'. 

Swap is a memory extender. If the machine is running low on real memory, it will use the swap space in stead. Works fine, but of course it is much slower. If you have heard a lot of hard disk activity when giving your machine a heavy work load,it could be because of swapping. 

Swap is a partition, and /home is a folder (or directory). There is no connection between these two.

I would not consider 5 GB too much for swap.

---

### Post by steve19137 on 2009-12-04
> **mörgæs said:**
> If you run ```
sudo fdisk -l
``` you will see the sizes of your partitions. Most likely one is marked 'swap'. 

Swap is a memory extender. If the machine is running low on real memory, it will use the swap space in stead. Works fine, but of course it is much slower. If you have heard a lot of hard disk activity when giving your machine a heavy work load,it could be because of swapping. 

Swap is a partition, and /home is a folder (or directory). There is no connection between these two.

I would not consider 5 GB too much for swap.

ah! that makes sense. thanks. 

also the other guy how posted about the home sharing of itunes, i already know how it works. but thanks for the links anyway, especially the pandora one :D

---

