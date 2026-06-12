---
title: "can't access hard drive"
date: 2011-05-16
forum: General Help
---

### Post by jlh68 on 2011-05-16
Well I screwed up and removed Ubuntu OS from my hard drive.  Now I cannot access any partition on the HD (I had set up several partitions).  I also can not install a new version of Ubuntu on the root partition.  I have tried to doctor it with "Disk Utility" and "GParted" without success.  I took the HD out of the tower and hooked it up externally to my laptop and the HD is not recognised by my laptop.  None of the partitions are recognised.  I have some files that I would like to recover, but not many as it was a new installation.  The Ubuntu install routine, Disk Utility each see the size, number of blocks and something else of each partition but not the names or other data.

I was wondering if any one had any suggestions as to how to repair or restore the HD?

---

### Post by tmette on 2011-05-16
Windows won't recognize the ext4 structure.  Have you tried booting the computer by a Live CD and then pulling the contents off?  The Live CD will also be able to re-format or partition the drive.

---

### Post by jlh68 on 2011-05-16
> Windows won't recognise the ext4 structure.I am not sure what you are saying with this sentence.  Is it a statement of fact? If so I already knew that windows doesn't see ext4. I do not have Windows on the computer. If it is a question then see the previous sentence. 

As for using a live CD, yes that is how I have used both GParted and Disk Utility.  I do not want to format the whole drive as I am trying to recover the few files that are on my /home partition, and some pictures on my /photos partition.  The other partitions are /video and it is empty, /var, /scratch, and /temp none of which have files I want to save.  I have tried to reformat just the / partition.  

I think it is strange that my partitions are numbered and the sizes recognised but nothing else.

I feel my problem may lie in the boot or MBR.

---

