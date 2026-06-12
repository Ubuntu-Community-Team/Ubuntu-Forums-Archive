---
title: "Disk space disappeared"
date: 2011-03-11
forum: General Help
---

### Post by parag14 on 2011-03-11
This is what happened...

I have a 30 GB ubuntu partition but i was getting warnings about less disk space remaining, when according to me i should have had 15gb space left. so i checked with disk utility, which did not help me. Then i installed xdiskusage, which showed those 15gb as permission denied. before i could begin to check for the source, everything crashed because my disk became full, and i am now not even able to login. can anyone tell me why is the 15-16 gb space showing up as permission denied, and how can i reclaim that space.
i couldnt take a snapshot, but found this one on the net which closely resembled my situation.

---

### Post by ~Plue on 2011-03-11
it could be the root trash... (just a possibility)
boot using a live cd, mount the partition and run[I] gksu nautilus
[/I]then, see if there are any files in .local/share/Trash/files which is located within the 'root' folder of that partition
(press ctrl+H to see hidden folders/files)

---

### Post by mssever on 2011-03-11
Also, after mounting the partition from the live CD, run baobab (possibly as root). It's a great way to quickly find where your disk space is going.

---

### Post by dnguyen1963 on 2011-03-11
> **parag14 said:**
> This is what happened...

I have a 30 GB ubuntu partition but i was getting warnings about less disk space remaining, when according to me i should have had 15gb space left. so i checked with disk utility, which did not help me. Then i installed xdiskusage, which showed those 15gb as permission denied. before i could begin to check for the source, everything crashed because my disk became full, and i am now not even able to login. can anyone tell me why is the 15-16 gb space showing up as permission denied, and how can i reclaim that space.
i couldnt take a snapshot, but found this one on the net which closely resembled my situation.

Did you happen to use K9copy or similar program to burn DVD?  K9copy creates backup files in the Temp folder of each DVD; however, it does not delete them afterward.  You must delete those files manually.

---

### Post by r.osmanov on 2011-03-11
What if you mount all and
```
$ df -h
```?

---

### Post by parag14 on 2011-03-11
> **dnguyen1963 said:**
> Did you happen to use K9copy or similar program to burn DVD?  K9copy creates backup files in the Temp folder of each DVD; however, it does not delete them afterward.  You must delete those files manually.

no, i definitely havent done anything like that...i have never even once used ubuntu to write a dvd..

---

### Post by parag14 on 2011-03-11
> **mssever said:**
> Also, after mounting the partition from the live CD, run baobab (possibly as root). It's a great way to quickly find where your disk space is going.

thanx, that did it...
i found a file called doodle.db of size 18 gb in /var. i deleted it and everything is now up and running..
any idea though how that file came there??

---

### Post by mssever on 2011-03-12
> **parag14 said:**
> thanx, that did it...
i found a file called doodle.db of size 18 gb in /var. i deleted it and everything is now up and running..
any idea though how that file came there??

I did a Google search, and it appears that doodle.db comes from Doodle, a desktop search engine. I presume that you installed it and either it is misconfigured or buggy.

---

