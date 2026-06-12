---
title: "putting 9.04 on my desktop, dual boot help"
date: 2009-06-29
forum: General Help
---

### Post by Addikit on 2009-06-29
When going through the installation with the live cd, I am not given the option to resize my partition of Windows XP (NTFS), as shown in the screen shot. The only option that seems to make sense for this situation is "Specify partitions manually" which I don't exactly want to mess with given I don't want to screw up my partitons =P

So.. What the heck do I do?

---

### Post by itsjareds on 2009-06-29
You actually DO want to specify partitions manually.. I was tentative to press that as well when I was installing. It actually just opens GParted, a partition editor. There, you can resize your Windows partition safely.

--

If you get an error about not being able to resize the Windows partition, go back into Windows and turn off paging files and defragment your hard drive using [PerfectDisk]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/learn-more"). I'm telling you to use a 3rd-party program to defragment because PerfectDisk can consolidate free space very well. Just download the trial.

Run PerfectDisk and defrag using the settings Consolidate freespace. [See this screenshot]("http://i40.tinypic.com/28qympk.png") to be sure. Once it's done defragging (this may take a while), your drive should show up with all of the colored blocks at the very top of the drive. If not, and there are gray blocks, you'll have to defrag system files. There's a button at the top of the window that should schedule that for the next reboot.

After all of this, your drive should be ready to be shrunk. Try going back to the Ubuntu installer and shrink your partition.

---

### Post by Addikit on 2009-06-29
> **itsjareds said:**
> You actually DO want to specify partitions manually.. I was tentative to press that as well when I was installing. It actually just opens GParted, a partition editor. There, you can resize your Windows partition safely.

--

If you get an error about not being able to resize the Windows partition, go back into Windows and turn off paging files and defragment your hard drive using [PerfectDisk]("http://www.perfectdisk.com/products/home-perfectdisk10-home-edition/learn-more"). I'm telling you to use a 3rd-party program to defragment because PerfectDisk can consolidate free space very well. Just download the trial.

Run PerfectDisk and defrag using the settings Consolidate freespace. [See this screenshot]("http://i40.tinypic.com/28qympk.png") to be sure. Once it's done defragging (this may take a while), your drive should show up with all of the colored blocks at the very top of the drive. If not, and there are gray blocks, you'll have to defrag system files. There's a button at the top of the window that should schedule that for the next reboot.

After all of this, your drive should be ready to be shrunk. Try going back to the Ubuntu installer and shrink your partition.


Thanks for the information =D if I decide to install windows and then dual boot I'll do that, but I got a little impatient and just decided to wipe windows. The only thing keeping me with windows was my Zune, I pretty much <3 Zune Social, but I figure I can get the same thing from Last.FM and the like and I can just buy another mp3 player.

Thanks for the help :) and wish me luck on being Windows free =/

---

### Post by itsjareds on 2009-06-29
Haha, no problem. I would have been Windows-free for a year now if it weren't for my buggy wireless. Good luck, you can message me if you need help later.

---

### Post by Addikit on 2009-06-29
> **itsjareds said:**
> Haha, no problem. I would have been Windows-free for a year now if it weren't for my buggy wireless. Good luck, you can message me if you need help later.

Thanks :)

---

