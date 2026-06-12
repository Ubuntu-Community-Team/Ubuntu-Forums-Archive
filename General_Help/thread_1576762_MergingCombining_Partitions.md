---
title: "Merging/Combining Partitions"
date: 2010-09-17
forum: General Help
---

### Post by inulled on 2010-09-17
Hi all,

I have a Linux partition table that is a little messed up. I have several unallocated segments. Knowing I only have 1.2GB left on my current Linux build, I need a way to merge these segments. I'm not too familiar with many of the alternatives to the popular Debian partition managers/editors (e.g. gParted). Does anybody know of an application in which allows me to merge the unused space with my current build?

Thanks in Advance!
 - Mike

---

### Post by john newbuntu on 2010-09-17
I wish you had listed the output of "sudo fdisk -lu" or you could have even installed gparted ("sudo apt-get install gparted" and attached an image of it after launching it.
I do not know of any way to merge partitions but resizing it is one option.  Copying the data to another drive and re-partitioning the existing drive is another option.

---

### Post by inulled on 2010-09-18
that bytes. you think that could be an option. :(

---

### Post by coffeecat on 2010-09-18
> **inulled said:**
> you think that could be an option. :(

Post the output of 'sudo fdisk -lu' and/or a screenshot of what Gparted shows, and someone might be able to advise you what your options are. :wink:

---

### Post by inulled on 2010-09-18
ohh and ill run the fdisk test here in a few if that will help...

---

### Post by inulled on 2010-09-18
okay

---

### Post by inulled on 2010-09-18
[IMG]http://i53.tinypic.com/27xmgeh.jpg[/IMG]

---

### Post by coffeecat on 2010-09-18
You cannot merge non-contiguous space. However, you have three swap partitions! If you can find out which one is being mounted in fstab, and if it's not sdb9, I would delete sdb9. Then you would be able to enlarge sdb8 into the freed space, and whatever of the 99.76 GiB unallocated space you want to use.

Having said that - that partition layout is a mess. If it was my machine I would backup all my personal data, create a new partition layout and make a fresh installation. But that's just me. Others may offer you other options.

**Edit:** had another look at the screenshot. From the lock icon against sdb9, I would guess that is the one mounted from fstab. Which means you'll have to edit fstab if you delete sdb9. You can do all that (and run Gparted) from the live CD, but it's another thing to consider.

---

### Post by inulled on 2010-09-18
lol yeah it is a mess. i think this might be my project for this weekend. sitting on 900MB of free space right now isn't to handy haha. thanks for the help man

---

### Post by strakarts on 2010-09-20
Hi,

Similar problem here (see attached image), which I've been living with for a little while but has always been bugging me.  It's also complicated by the NTFS partitions, which contain my Windows 7 OS (which I want to keep!), and files. 

But I'd really like to get back that "unallocated" space!
Is the answer the same?  (Need to rebuild partition table?)

---

### Post by coffeecat on 2010-09-20
Hi, and welcome to the forum.

Yours is a simpler problem that the OP's but the answer to your question  depends on what you what to do with the 10.68 + 74.5 GiB of unallocated space in your extended partition. At the moment you can't create one partition with it because it's not contiguous. But if you did want to make another partition, the simplest way is to boot up with the live CD and open Gparted. Then right-click on the swap partition and choose 'swapoff' (it will have been mounted by the live CD automatically) and then move the swap partition up so that it abuts the NTFS sda5 partition. Then you'll have ~85GiB of contiguous space in which you can make as many logical partitions as you wish.

Moving swap like this  will take some considerable time. It would be quicker to delete the present swap partition and make a new one next to the ntfs partition, but the new one would have a different UUID. If you are comfortable with UUIDs and editing /etc/fstab, this might be the way to go. Otherwise simply move the swap partition.

A couple of general comments. Windows is on sda2, a primary partition, and that's how it should be. Unless you use a bit of gee-whiz trickery, Windows needs to be on a primary partition. However, Linux doesn't. It's quite happy to boot from a logical partition, but I see that you have your Linux root partition on a primary: sda4. No problem with this, but I prefer to leave Windows with whatever primary partitions the computer manufacturer sets it up with (3 in the case of my Acer laptop :roll:) and then create one large extended in which I can create as many logicals as I need for Linux and/or data partitions. I find this more flexible. You can quickly run out of your allowed four primaries in a mbr partition table. Windows is happy for its D:/E:/whatever NTFS partition to be a logical one - as I see you have.

Post back if you need any further help. Good luck!

---

### Post by strakarts on 2010-09-20
Thank you for the outstanding welcome, coffeecat.  Extremely useful comments/advice.
I think I'll try moving the swap (as soon as I find the time), and will keep you posted on how that goes!

---

### Post by strakarts on 2010-09-20
Update: 

I successfully moved the swap partition as suggested, and converted my 10.68 GB to another logical drive, but I then realized that the unallocated 74.50 GB are not currently part of the existing extended partition (sda3).  So at this point I still can't do anything with that unallocated space because, as you mentioned earlier, I am restricted to four primary partitions.  

Any suggestions?  (Simple is best, as I am new to this sort of thing!)

In an earlier post, you recommended just running Linux from a logical (or several logicals) within the extended partition, rather than having it on a primary partition.  How would you go about setting this up from my current configuration?

---

### Post by coffeecat on 2010-09-21
> **strakarts said:**
> Update: 

I successfully moved the swap partition as suggested, and converted my 10.68 GB to another logical drive, but I then realized that the unallocated 74.50 GB are not currently part of the existing extended partition (sda3).  So at this point I still can't do anything with that unallocated space because, as you mentioned earlier, I am restricted to four primary partitions.  

Any suggestions?  (Simple is best, as I am new to this sort of thing!)

Apologies for missing that the extended didn't cover all of the space beyond the primaries. It was there in the screenshot. #-o

:wink:

Anyway.... I'm fairly sure that you can simply enlarge the extended partition (sda3) to include that space, and then create one or more logicals in the enlarged extended partition. I'm not in Ubuntu atm with access to Gparted so I can't double-check this, but (from the live CD) unmount swap as before, and (iirc) select sda3, and then Partition > Resize/Move. Increase the number in the middle box so that the number in the third is zero. As with any partitioning, backup everything because things can go wrong.

> **strakarts said:**
>  In an earlier post, you recommended just running Linux from a logical (or several logicals) within the extended partition, rather than having it on a primary partition.  How would you go about setting this up from my current configuration?

This is only for flexibility for the future. If you can get sda3 to reclaim that space then I would leave things as they are, because it would involve a reinstall of Ubuntu. But if you did want to do a fresh install, backup everything on sda5, and delete (from live CD) every partition except sda1 and sda2. Then create an extended in the whole of the unallocated space, and as many logicals as you might need, including a data/ntfs. Then use the manual option at the partitioning stage of the installer to use the partitions you have already set up.

Windows might throw a minor wobbly at finding that its "E:" or whatever partition has gone walkabout, but that shouldn't be too much of a problem.

But that's all fairly drastic. If you can extend the extended so to speak, that should do nicely.

Good luck!

---

### Post by strakarts on 2010-09-26
Finally found the time to play around with this some more.  You were completely correct!  I simply "extended the extended" and everything is now peachy!  Thanks again for your help, coffeecat.

And good luck with your Schrödinger's box situation; that'll be a bit harder to solve!
 ;)

---

### Post by coffeecat on 2010-09-26
> **strakarts said:**
> And good luck with your Schrödinger's box situation; that'll be a bit harder to solve!
 ;)

:lol:

---

### Post by inulled on 2010-09-26
yeah it is similure in a way. just without the NTFS partition. I actually just installed a fresh copy of Ubuntu. problem solved:KS

---

### Post by inulled on 2010-09-26
ohh dang i did not see all those posts lol

---

