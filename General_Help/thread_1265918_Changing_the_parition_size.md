---
title: "Changing the parition size?"
date: 2009-09-14
forum: General Help
---

### Post by gordong11 on 2009-09-14
I have a single 150gb WD raptor, where I have Vista and 9.04 installed on a dual boot loader. 

I wasn't expecting to like 9.04 as much as I do, and only allocated 20GB for Ubuntu. Windows has 127GB allocated of which , 60GB is being used, after disk cleanup and defrag.

I'd like to add 40GB more to Ubuntu, but I'm scared I'm going to lose data. I have the Partition Editor installed on 9.04. I somehow have a third volume, of 18GB of "extended" file system. can I get rid of this 18GB, and allocate to Ubuntu without losing data?

Do I have use the use the Install CD? is there instructions on this?

In the meantime I'm downloading the gparted live CD on ISO. From what I can tell I have to increase the extended files system, then, add to sda5 from extended.

Thanks

---

### Post by nothingspecial on 2009-09-14
It depends what the 18gig partition is.

You should be fine resizing you partitions, especially after a defrag. But you`ve got to back all your data up. You should do this anyway but it is essential before you start editing partitions.

It can go wrong.

---

### Post by gordong11 on 2009-09-14
Well I did it, it went flawless..the steps I took:

1. Download GParted live from: 
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)
2. Burned ISO image to CD
3. re-started, changed boot order to DVD-Rom as 1
4. Boot Gparted and Pressed enter (used defaults in Gparted as it asked me questions)
5. Freed up (shrunk)30GB from NTFS volume, press apply
6. Added the 30GB to unallocated volume, then added to Sda5 in the same step. Press apply

Thats it! So impressive how easy it was, and only took about 10 minutes. I have all my files too :)

---

### Post by TheStroj on 2009-09-16
thank you so much for the help, I had 20 GB for Ubuntu and 470 for Windows 7, now i have 430 for Ubuntu and 60 for Windows 7 ^^

---

