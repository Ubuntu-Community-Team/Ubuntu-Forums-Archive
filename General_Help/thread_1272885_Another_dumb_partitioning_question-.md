---
title: "Another dumb partitioning question-"
date: 2009-09-22
forum: General Help
---

### Post by blur xc on 2009-09-22
Here's what my drive looks like (see attached screen capture)-

As you can see, my sda1 is WAY too big.  sda2 is my Vista partition, which I hardly use (but can't kill- yet), and it's a bit big too, but not that bad.  sda3 is my /home partition.  Is there anyway to shrink sda1 and add that to sda3??  Would I have to make images of my disk, blank it- do it over, and write the images back onto the new partitions?  that scares me a bit...  anyway, thanks...


Interesting side note, btw- compare the sizes of the vista and ubuntu install.  I'm an apt-get whore too, I install anything and everything that sounds cool, and it's only like 7gigs, compared to the base install of vista's 30gigs...and that's w/o ms office installed either.  Just vista home premium, and FF, some anti-virus, malware, and lgihtroom, etc..

BM

---

### Post by CatKiller on 2009-09-22
> **blur xc said:**
>  Is there anyway to shrink sda1 and add that to sda3??

Yes, but not from within your normal environment. You can't change a partition that's mounted, and your / partition is necessarily mounted if you're running Gparted from it. Use a live cd; either your Ubuntu install disk or the [Gparted live cd]("http://gparted.sourceforge.net/livecd.php").

You don't need to nuke them. Just shrink them and shuffle them along.

You might need to use Windows' own partitioning tool to resize the NTFS partition. NTFS is still Microsoft's Secret Sauce. Or do what the people that wrote Gparted [suggest]("http://gparted.sourceforge.net/faq.php"):

> When resizing boot NTFS partitions, it is advisable to perform this as a single operation only. After resizing, boot into Windows twice to allow Windows to perform its checking operations. 

---

### Post by blur xc on 2009-09-23
> **CatKiller said:**
> Yes, but not from within your normal environment. You can't change a partition that's mounted, and your / partition is necessarily mounted if you're running Gparted from it. Use a live cd; either your Ubuntu install disk or the [Gparted live cd]("http://gparted.sourceforge.net/livecd.php").

You don't need to nuke them. Just shrink them and shuffle them along.

You might need to use Windows' own partitioning tool to resize the NTFS partition. NTFS is still Microsoft's Secret Sauce. Or do what the people that wrote Gparted [suggest]("http://gparted.sourceforge.net/faq.php"):

So then, what would be the proper order of things?

Boot to the live cd- resize sda1.

Boot to the vista install cd??  and run the MS partitioner to resize the vista partition?

then go back to the live cd to finish the job?

how should I back up the data before I cut loose?  Should I make ISO images of sda1 and sda2 before I start just in case?  sda3 is just data, so I could just tar that to my external drive for good measure...

Sorry for all the questions.  I'm still pretty new to partitioning.

Thanks for the help,
BM

---

### Post by CatKiller on 2009-09-23
> **blur xc said:**
> So then, what would be the proper order of things?

I couldn't tell you for sure. The last (and only) time I tried to re-size the Windows boot partition, I managed to break Windows. It just decided (for reasons it didn't want to explain) that it wouldn't boot any more. Since I'd already moved to Ubuntu full-time and I'd warned my housemates of the possibility, I didn't bother to fix it. I just nuked the Windows install and carried on as before.

The way that makes most sense from what the Gparted page says is pretty much as you've described. You could resize and then move the NTFS partition in two passes with Gparted, booting into Windows between the two, but if you're doing that you might as well do it in Windows. Although I have no idea what partitioning tools come with Windows.

I'm not sure that ISO images would work, since the data isn't structured like a CD. But something like that. Straight data is easy to back up and easy to restore if it all goes pear-shaped, and tar will definitely be fine for that. Basically, if you plan to have everything safe that you would need (data, installation files, emails and so on) to get back up-and-running should you have to re-install both Ubuntu and Windows, then that should be sufficient for anything in between.

Good luck!

---

