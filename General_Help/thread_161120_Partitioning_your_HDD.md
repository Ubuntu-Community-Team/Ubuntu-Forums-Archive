---
title: "Partitioning your HDD"
date: 2006-04-16
forum: General Help
---

### Post by drpolish on 2006-04-16
What is the ideal setup for a linux system?
I have been partitioning my linux system by having two distros (gentoo/ubuntu) and having two root directories. 
It hasn't been since recently that i realized i can have seperate /home and other directories seperate. 
What is the IDEAL linux setup for say .. a 100 gb HDD?

---

### Post by Ramses de Norre on 2006-04-16
Keeping /home seperate is very usefull to keep your data when reinstalling for some reason.

---

### Post by chettyk on 2006-04-16
[QUOTE=drpolish]What is the ideal setup for a linux system?[/QUOTE]

I don't think there is anything like an *ideal* linux set up. The best set up depends on your use of the system. 

I have Ubuntu on both my personal workstation and laptop. For both computers I have separate partitions for the root file system, swap and for home. 

Having /home on a separate partition allows me to reinstall linux without losing my personal files and settings. So whenever Ubuntu issues a new release, I prefer to do a fresh install rather than upgrade the existing one.

I have a 80 GB hard drive on my desktop. I use 20 GB for the root partition, 2 GB for swap and have kept 40 GB for home. I keep the remaining space to try out linux distributions that catch my fancy.

---

