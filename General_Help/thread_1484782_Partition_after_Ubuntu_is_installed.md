---
title: "Partition after Ubuntu is installed"
date: 2010-05-16
forum: General Help
---

### Post by mindlessbrain on 2010-05-16
Hello all,

I just got Ubuntu installed as a dual boot with Vista. yay! It seems to run fine and all that. I can get into both Vista and Ubuntu with no problems. 

My computer has two separate 500 gig hard drives. I have Vista on one, and Ubuntu on the other. This is all well and good, except that I won't be using 500 gigs of Ubuntu. (I'm primarily using it to run BioPerl.) How can I partition my D: drive to have say 200 gigs of Ubuntu and 300 of swap/shared/whatever it is? 

Thanks so much!
MB

---

### Post by Bill magee on 2010-05-16
GParted will do it.

---

### Post by mindlessbrain on 2010-05-16
Awesome! Thanks. I just open up Ubuntu, open a terminal, and type 

sudo apt-get install gparted

Right? Once I get the program going I'll probably be fine. 

Thanks again!

---

### Post by Bill magee on 2010-05-16
That's about it. Make sure you have your data backed up.

And one other thing: make sure you have your data backed up!

---

### Post by mindlessbrain on 2010-05-16
Thanks! Before I started this big project I made sure I had everything backed up. Gotta love the terabyte external hard drive. =)

---

### Post by plucky on 2010-05-16
You cannot resize the Ubuntu Partition from within Ubuntu as it is mounted.Use the Live CD as that already has gparted installed and the partitions aren't mounted,except the swap partition.

Good Luck

---

### Post by Bill magee on 2010-05-16
Thanks Plucky, I should have known that.

---

### Post by ryan858 on 2010-05-16
By the way, you will never need 300 GB of swap... you only need a maximum of the size of your RAM... For example if you have 4GB of RAM installed, you only need *at most* a 4 GB swap partition... You really don't even *need* that much, only like 512mb, or 1 GB, but since you have so much space, I'd say just go with 4 GB.

However, this does depend on your situation. For example if you're going to be doing a lot of RAM-intensive stuff, like video editing, you might want a swap that will fit your needs. Video authoring and stuff like that can require up to 6-8 GB of RAM/Swap... Although, if you're *mapping the known universe* you may need 300 GB!

(BTW, Swap is basically like Windows' PageFile)

---

