---
title: "Dual booting Ubuntu 11.04 with Backtrack 5"
date: 2011-10-18
forum: General Help
---

### Post by SeaHawk22 on 2011-10-18
I have Ubuntu 11.04 installed on my entire hard drive, I would like to dual boot with Backtrack 5.
     
* Best program to partition drive

* What is the best way to approach this? I use to dual boot windows, and Ubuntu many moons ago, and I use to have a window that popped up with the linux icon, and windows icon, which allowed me to choose which OS I wanted to boot but I forget how I did this.

* If there is a step by step tutorial for the process, please direct me if so, I could not find such.

Thank you,

---

### Post by Bmonsterboy on 2011-10-18
Hey man, Backtrack FTW. 
I would suggest using Gparted in ubunto to create yourself an extended partition with separate logical partitions for boot data for both OS's, a primary for swap space, and another primary for your home drive (but only if you wish to use the same home directory for both ubuntu and backtrack). Have a look [here]("https://help.ubuntu.com/community/HowtoPartition") for general partitioning info, and [here]("http://www.dedoimedo.com/computers/gparted.html") for a good place to start with Gparted.
When it comes to installing... i'm not sure wether backtrack 5 has a graphical side-by-side install, otherwise you will just have to manually specify partitions.
 
Hope this can get you started.

---

### Post by Dangertux on 2011-10-18
> **Bmonsterboy said:**
> Hey man, Backtrack FTW. 
I would suggest using Gparted in ubunto to create yourself an extended partition with separate logical partitions for boot data for both OS's, a primary for swap space, and another primary for your home drive (but only if you wish to use the same home directory for both ubuntu and backtrack). Have a look [here]("https://help.ubuntu.com/community/HowtoPartition") for general partitioning info, and [here]("http://www.dedoimedo.com/computers/gparted.html") for a good place to start with Gparted.
When it comes to installing... i'm not sure wether backtrack 5 has a graphical side-by-side install, otherwise you will just have to manually specify partitions.
 
Hope this can get you started.

Backtrack 5 uses the ubiquity installer, which is the same as Ubuntu, so you could partition the same way you would if you were installing Ubuntu.

---

### Post by SeaHawk22 on 2011-10-18
> **Dangertux said:**
> Backtrack 5 uses the ubiquity installer, which is the same as Ubuntu, so you could partition the same way you would if you were installing Ubuntu.

Are you referring to the guided installer that is available when installing Ubuntu?

---

### Post by SeaHawk22 on 2011-10-20
bump

From the research I have done, I found that it is possible by shrinking Ubuntu's partion, and after installing Backtrack you need to update the Grub, that is what I am hesitant to do, has anyone done this with any success?

---

