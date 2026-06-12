---
title: "Where's All My Disk Space?"
date: 2009-06-27
forum: General Help
---

### Post by thefunks on 2009-06-27
When I installed Ubuntu I thought I selected 8GB as the size for the partitioned drive. I am trying to burn a full length dvd with top quality video in Devede and it is saying I only have like less than one.and a half gigs available.

I've included a screen shot of gpart and I'm just struggling to understand how to tell which partition is which.

---

### Post by philcamlin on 2009-06-27
how much apps do you have installed?

how much music do you have?

do you have a huge dvd collection?

right clock on home and click properties. how big is it :popcorn:

---

### Post by thefunks on 2009-06-27
Oops, here's a less obstructed screen shot.

---

### Post by thefunks on 2009-06-27
I don't have any music or video in my ubuntu disk space yet. I have just a few extra programs that didn't come with the standard installation, like Wine and Devede and maybe a couple other small ones. Virus checker. I have used hardly any space.

**_HOME_**

Contents: 50 items totalling 698MB

Volume: Unknown

Free Space: 1 .1 GB

---

### Post by philcamlin on 2009-06-27
8gb thats it? atleaast 20 is recommended

4gb base ubuntu install size + 700mb home +video size? 700mb and 1.6 gb swap 

thats about right 1.1 gb free :P

nothings a mystery its all used up :(

---

### Post by thefunks on 2009-06-27
LOL alright well then is there a way I can increase the size of my partition without reinstalling? I want a bigger partition so how would I go about managing what I've got now to get there? If I have to reinstall, do I have to delete the partition manually etc and how would I do that?

---

### Post by Agent ME on 2009-06-27
Applications -> Accessories -> Disk Usage Analyzer

This program is very useful in figuring out what is using your hard drive space.

---

### Post by philcamlin on 2009-06-27
> **Agent ME said:**
> Applications -> Accessories -> Disk Usage Analyzer

This program is very useful in figuring out what is using your hard drive space.

or... you can boot into live cd and do it that way 

im not sure about making it bogger ive never had to do such a thing :popcorn:

---

### Post by CatKiller on 2009-06-28
There's no Linux drive in your screenshots. Have you got a second hard drive, or did you install using Wubi? The methods to change the drive size differ depending on how you've installed it.

8 GiB is unlikely to be enough space to burn a DVD, since the act of burning creates a temporary image which is nearly 5 GiB for a full DVD.

---

