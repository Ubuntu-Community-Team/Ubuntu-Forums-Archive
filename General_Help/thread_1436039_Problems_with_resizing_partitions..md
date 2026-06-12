---
title: "Problems with resizing partitions."
date: 2010-03-22
forum: General Help
---

### Post by Hikayu on 2010-03-22
Yo all,

Ok, yesterday I had several problems (now all solved :) ) and created a new partition of around 50 gigs (out of the whole 200 gigs for my HD) with Ubuntu Lucid (10.04 Beta 1 to be precise).

I've begun transferring all data I need and want from my previous now unwanted partition. However, before being rash and deleting the partition as a whole, I decided to shrink it down to the smallest size possible and and extend the partition I'm using now with the unallocated space.

Now : The problem.
I'm not able to resize the partition. The "resize/move" button is grayed out.

And *YES*, I'm using a LiveCD (Um, a LiveUSB in this case) to perform all the partitioning. And here's the additional information :

[http://img2.imageshack.us/img2/1473/screenshotsd.png](http://img2.imageshack.us/img2/1473/screenshotsd.png)


Oh yes, and the reason why I don't want to delete the partition YET is because I'll leave it on for a week and see what data I've forgotten to take.

---

### Post by plucky on 2010-03-22
> **Hikayu said:**
> Yo all,

Ok, yesterday I had several problems (now all solved :) ) and created a new partition of around 50 gigs (out of the whole 200 gigs for my HD) with Ubuntu Lucid (10.04 Beta 1 to be precise).

I've begun transferring all data I need and want from my previous now unwanted partition. However, before being rash and deleting the partition as a whole, I decided to shrink it down to the smallest size possible and and extend the partition I'm using now with the unallocated space.

Now : The problem.
I'm not able to resize the partition. The "resize/move" button is grayed out.

And *YES*, I'm using a LiveCD (Um, a LiveUSB in this case) to perform all the partitioning. And here's the additional information :

[http://img2.imageshack.us/img2/1473/screenshotsd.png](http://img2.imageshack.us/img2/1473/screenshotsd.png)


Oh yes, and the reason why I don't want to delete the partition YET is because I'll leave it on for a week and see what data I've forgotten to take.


Which partition do you want to resize?

If it is /dev/sda5,you will need to turn swap off before you can resize any partition within the extended partition.Right click on the swap partition and select swapoff

Good Luck

---

### Post by Hikayu on 2010-03-22
Sda1. 


Sry, my bad. I forgot to include that.

---

### Post by Hikayu on 2010-03-22
> **plucky said:**
> Which partition do you want to resize?

If it is /dev/sda5,you will need to turn swap off before you can resize any partition within the extended partition.Right click on the swap partition and select swapoff

Good Luck

Nvm, You were still correct. Jesus, I can stupid. The answer was right in front of me.

I turned swap off and it works

Cheers,
Hikayu :)

---

