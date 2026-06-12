---
title: "Redistribute space between partitions using gparted"
date: 2010-07-08
forum: General Help
---

### Post by sjmacewan on 2010-07-08
Hi there,

A year ago when I set up my laptop, I wasn't sure how much space I wanted to have for each of my two partitions, one for Vista and one for Ubuntu.

As a result I allocated too little to my Windows partition and would like to change this, as long as it doesn't involve a clean restart (not worth the headaches of reinstalling some of the stuff I've had to install...)

I've attached a screenshot of the gparted screen outlining my current set-up. What I'd like to do is make sda5 smaller by about 35 GiB or so and let sda2 occupy that space.

I'm a bit unsure as to whether or not this will be as easy as one might think, because I'd want free space from the "start" of sda5...will gparted know to "shift" it down, or if I want to shrink it will it just chop it off of the end, where sda2 couldn't spill over into.

Cheers,

Scott

---

### Post by bodhi.zazen on 2010-07-08
It should be easy.

With the live CD run gparted, unmount the swap partition.

First shrink sda5 -> apply changes

Then shrink the extended partition -> apply changes.

Then increase the size of your windows partition.

---

### Post by sjmacewan on 2010-07-08
Thanks for the fast response!

I was thinking that THAT would work, but I'd rather be safe than sorry.

A question though: why would I need to unmount the swap partition? What does this accomplish?

The whole concept of a swap partition is lost on me, please forgive my ignorance.

---

### Post by lmarmisa on 2010-07-08
GParted is able to shrink your partition sda5 and enlarge sda2 using the free space that is now occupying sda5. But be very carefull because you will need to shrink and move not only sda5 but also the extended partition sda3.

You will need a Ubuntu Live CD too.

I recommend to make a backup ([http://clonezilla.org](http://clonezilla.org)).

Kind regards,

Luis

---

### Post by sjmacewan on 2010-07-08
Right, lmarmisa, of course. I suppose I should have been more clear in my original post. What I want is to shrink sda3 (which contains nothing but sda5) and let sda2 spill over into that space.

I'm going to give this thread a few hours of time to get feedback from other people if they have something to say, and then give bodhi.zazen's algorithm a shot and post the results.

Still, I'd like some clarification on why one should unmount the swap...

---

### Post by lmarmisa on 2010-07-08
You will need to execute several GParted commands (or several steps). Take into account that the extended partition sda3 and the logical partition sda5 are considered as independent partitions by Gparted.

You cannot modify the root partition while you are running Ubuntu in it. So, you will need to boot from an Ubuntu Live CD. You do not need to swap off if you do not plan to modify the swap partition.

A last comment: if you modify the swap partition, its UUID will be changed and you will need to update the /etc/fstab with the new UUID.

Kind regards,

Luis

P.S. Do not forget to make a save Backup before to reconfigure your partitions.

---

### Post by bodhi.zazen on 2010-07-08
You need to unmount the swap partition because you can not resize a partition while it is mounted.

If the swap partition is mounted you will not be able to resize the extended partition.

You can do everything from the gparted menu (graphically).

---

### Post by lmarmisa on 2010-07-08
Hi bodhi.zazen,

The swap partition is a primary partition and it is out of the extended sda3 partition. 

So, it will be not needed to unmount it.

---

### Post by bodhi.zazen on 2010-07-08
> **lmarmisa said:**
> Hi bodhi.zazen,

The swap partition is a primary partition and it is out of the extended sda3 partition. 

So, it will be not needed to unmount it.

I did not catch that, thank you.

Unusual configuration (Ubuntu almost always places swap in the extended partition).

---

