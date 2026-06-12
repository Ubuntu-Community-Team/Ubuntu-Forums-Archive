---
title: "Partition help"
date: 2010-12-17
forum: General Help
---

### Post by Divine E on 2010-12-17
Hey guys, so I recently got a new laptop.  Satisfied with my Ubuntu experience on the Desktop, I have decided to continue using Ubuntu on my new laptop.  So I went ahead and split my partition in two, one for windows, and one for Ubuntu.  What I didn't realize was that I in fact did not split it in two.  I Just found out that half of my 500 Gb hard drive was unused.  I of course, wanting to get the most out of my money, want to utilize my full hard drive.  I would like to assign parts of the 250GB partition left to each OS.  (Probably more to Ubuntu considering I tend to use it more)  I booted into the old Ubuntu 10.04 Live disk to use G-parted to fix the situation, but to be honest, my knowledge of partitions is limited, and I can't quite figure out how to do this.  I already have a lot of data on both Windows and Ubuntu, and I would like to keep it all if possible.  Last time I attempted to use G-parted I somehow ended up messing up my entire PC, and had to start Ubuntu again from scratch.  

Help very much appreciated.

-Divine E

(Attachment is a screenshot of G-parted from live CD.)

---

### Post by dabl on 2010-12-17
Here's good guidance: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Divine E on 2010-12-17
Ugh, I'm sorry, I must sound like a n00b, but I guess I kinda am.  That article was somewhat helpful, but I still am having trouble.  Can anyone provide a quick step by step?  Like I said, I really want to be able to keep all my data.

---

### Post by cbilljones on 2010-12-17
> **Divine E said:**
> Ugh, I'm sorry, I must sound like a n00b, but I guess I kinda am.  That article was somewhat helpful, but I still am having trouble.  Can anyone provide a quick step by step?  Like I said, I really want to be able to keep all my data.

well its not going to be really possible to merge half to each OS, as the space would need to be continuous; im going to recommend formating the unpartitioned space as NTFS as having a 232gig drive that can be accessed by both OS'. We can do that right from ubuntu; Goto system>Administration>Disc Utility.
Select the empty space and pick "Format Volume" and set it to NTFS, click format and there ya go

---

### Post by Divine E on 2010-12-17
> **cbilljones said:**
> well its not going to be really possible to merge half to each OS, as the space would need to be continuous; im going to recommend formating the unpartitioned space as NTFS as having a 232gig drive that can be accessed by both OS'. We can do that right from ubuntu; Goto system>Administration>Disc Utility.
Select the empty space and pick "Format Volume" and set it to NTFS, click format and there ya go
Okay, well thank you very much.  I suppose that's as good as I will be able to get it.  lol.  I guess in reality It provides more versatility altogether.

---

### Post by cbilljones on 2010-12-17
> **Divine E said:**
> Okay, well thank you very much.  I suppose that's as good as I will be able to get it.  lol.  I guess in reality It provides more versatility altogether.

Ya, its a quick solution that also provides some advantages ;) there would be ways to do what you wanted but it would be many steps; and i wouldnt attempt it without a full backup first; in the future, no need to partition before install; the default install options were exactly what you wanted

---

