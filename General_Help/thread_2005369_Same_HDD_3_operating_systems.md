---
title: "Same HDD 3 operating systems"
date: 2012-06-17
forum: General Help
---

### Post by GreatDanton on 2012-06-17
Like the title says I want to have 3 operating systems on one Hard disk drive. I have 500 Gb sata drive on which I have Ubuntu and Windows7 installed. Now I want to shrink Ubuntu partition and install Backtrack linux. However if I shrink the partition I am not able to install Backtrack there, because it's says it's unusable.

After that I boot from live cd and I tried to format free space to ext4, however I was not able to do that (I got an error something like too much partitions- I don't remember the whole error, but I am pretty sure that you will know what is the problem).

Now the question:
Is it possible to shrink ubuntu partition and install backtrack linux or not -without formating the whole hard disk.

---

### Post by blackbird34 on 2012-06-17
Short version: 
"Too much partitions" - Sounds like you have reached your limit of 4 primary partitions on one Hard Drive.

Basically, you need to remove one of your "primary partitions" (not one with Windows on it!!) and create an "extended partition" (a kind of container for "logical partitions", which are basically a way of having partitions beyond the hardware limit 

More detailed version :D :
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Edit: ah, the question. Yes, once you have made yourself a (big enough) extended partition, you can install Backtrack Linux inside it, in a logical partition that you will be prompted to create.

---

### Post by GreatDanton on 2012-06-17
Thanks for reply.
I assumed that I will have to format my Ubuntu partition in order to install Backtrack. Because I don't want to format Ubuntu partition (making dual boot again) backtrack will have to wait :).

It's easier to buy another HDD and install it there.

Thread closed

---

### Post by Cheesemill on 2012-06-17
> **GreatDanton said:**
> It's easier to buy another HDD and install it there.
Or you could run BackTrack as a VM.

---

