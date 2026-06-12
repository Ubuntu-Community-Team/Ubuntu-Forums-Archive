---
title: "Partitioning help."
date: 2010-02-27
forum: General Help
---

### Post by ferret man on 2010-02-27
I know how to partition, I would just like to know if I *should* partition in a way like this:
A home partition (/home)
A swap partition 
A root partition   (/)
And...
A tmp partition? (/tmp)

I know the first three would be a good choice, but would the fourth be good, and how should I divide my system? I have a 16 GB hard drive. Which flags should I use? Please elaborate on whether I should do this or not. If I should, could you please include instructions that are easy to follow? Thank you very much.

---

### Post by gordintoronto on 2010-02-28
Skip the tmp partition.  Your hard drive is quite small, and every extra partition generates a potential limitation.

My root partition is bigger than your hard drive, because it's a huge annoyance if the root fills up.  Mind you, I have also run Ubuntu on a 10 GB drive, with just a swap partition and root.

---

### Post by paxmark1 on 2010-02-28
16 gb I would strongly urge you to go with crunch bang linux.  It is a derivative based on 9.04 and open box.  Much smaller /      
It is not just for netbooks.  If you have a 16 gb hdd, I suspect you might be a little light on memory, cpu cycles, etc.   Crunch bang uses ubuntu repositories.  

of course you will have to make / bootable.    /swap gets set correctly with most any partitioning program.   

For my 4 gb ssd hdd netbook with crunchbang, I added a 16 gb sdhc card for   /home 

A usb stick could also be /home   I am using 57% of a 3gb / partition and I have 1gb of /swap.   I have open office and java installed on it.  

On my desktop with 9.10 Ubuntu with programs to compile programs, etc. 7gb is getting quite small for /   

9.04 works fairly good on older equipment.  

the command df will be your friend on this system as will du  Enjoy learning.

peace mark

---

### Post by ferret man on 2010-02-28
I think, like you do, I will use different hardware, like large capacity SD cards, seeing as how my netbook has an SD card slot. If I put my /home partition on the SD card, I will have a larger capacity for it, even if the card is only 5GB, my /home partition is currently only 3.7 GiB, however, I plan on getting a larger capacity SD card. I am also going to see if a computer store in my town can put a bigger hard drive on my Dell MIni 9.

---

