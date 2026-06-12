---
title: "Partition help"
date: 2009-08-13
forum: General Help
---

### Post by dvigue on 2009-08-13
I have been using ubuntu for a few days now and i love it. i need to redo my partitions. my XP partition is way to big, my swap is too small and i never created a seprate home partition.  could you all give me your opinions on how you would set it up? or resize them, i should say since it is already installed?  and would you back up first?

anyway, here is my set up

xp partition= 75 gigs, using only 15gigs
/Root partition for ubuntu=25gig partition
swap partition= 2 gigs
thats all for my linux partitions. should i have more?

i also have a "storage" partition of 150gigs, but i need that cause that is where i store everything. so i can take some away from my xp partition and add them to where ever.  please let me know your thoughts. i would like to resize this all tonight....

---

### Post by rhchia on 2009-08-13
> **dvigue said:**
> I have been using ubuntu for a few days now and i love it. i need to redo my partitions. my XP partition is way to big, my swap is too small and i never created a seprate home partition.  could you all give me your opinions on how you would set it up? or resize them, i should say since it is already installed?  and would you back up first?

anyway, here is my set up

xp partition= 75 gigs, using only 15gigs
/Root partition for ubuntu=25gig partition
swap partition= 2 gigs
thats all for my linux partitions. should i have more?

i also have a "storage" partition of 150gigs, but i need that cause that is where i store everything. so i can take some away from my xp partition and add them to where ever.  please let me know your thoughts. i would like to resize this all tonight....


i'm trying to anticipate what the pro will say. use gparted. haha...
anyway just to share with you. if you are not using multiple linux, there's not necessary a need to have a partition just for /home. and another thing is i realise you swap pretty slim. normally they go 2 times ur ram size. :)

---

### Post by dvigue on 2009-08-13
Oh yeah, i will use gparted for it. i know that, just not sure on the sizes, and how many to make...

one other thing, why the separate partition for home? what is the reason for that? storage in case of crash?

---

### Post by rbc on 2009-08-13
Backup? ABSOLUTELY!!!! And while it is not necessary to have /home on its own partition, it is safer; if you have to reinstall, then /home is left unscathed

---

### Post by dvigue on 2009-08-13
> **rbc said:**
> Backup? ABSOLUTELY!!!! And while it is not necessary to have /home on its own partition, it is safer; if you have to reinstall, then /home is left unscathed

good point...

since im new, what is the best and easiest back up utility for ubuntu???

---

### Post by michy99 on 2009-08-13
Since you are going to make a separate /home partition, 25 gig is plenty for Ubuntu. I would suggest shrinking Windows to whatever you think you need, and using the rest of the space for /home. After you make the partition, here is a guide to moving /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

