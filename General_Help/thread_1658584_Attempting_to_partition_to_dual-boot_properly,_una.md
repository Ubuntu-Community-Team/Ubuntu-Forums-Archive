---
title: "Attempting to partition to dual-boot properly, unable."
date: 2011-01-02
forum: General Help
---

### Post by camtom12 on 2011-01-02
Hi!  I'm running 10.04 on Wubi in XP and want to partition to dual boot properly.  I've done the permanent grub-update issue fix for Wubi so I've got the time to figure this out, I'm just at an impasse right now.

I've tried both GParted and PartitionMagic Live CDs and have been unable to shrink my main partition down.  It's currently at 45 or so GB with about 22 GB empty.  I've turned off my virtual memory in XP as well and no dice.  I keep getting the error in GParted during the shrinking process.  It doesn't really explain why, though.

Any ideas?

Thanks!
--Cameron

---

### Post by oldfred on 2011-01-02
How much are you shrinking it? Windows needs 20% free, so you really only have about 12GB available.

Have you run chkdsk on windows. I was able to boot windows XP without any issue but gparted did not like my XP partition. After chkdsk then gparted would see it.

---

### Post by supershin on 2011-01-02
You could also try running a defrag on XP before attempting to shrink the partition.

---

### Post by camtom12 on 2011-01-03
I didn't know it needed 20%!! nuts!

I defragged and ran chkdsk before I tried gparted. Oh well. Looks like I'm sticking to Wubi until I get a new laptop!

Thanks!

---

### Post by Bucky Ball on 2011-01-03
Your other option is to reinstall Windows with appropriate partition size, leaving the rest free space, then install Ubuntu in the free space creating these partitions:

/
/home
/swap

... at least.

---

### Post by oldfred on 2011-01-03
Wubi is just a big file in windows. How big is your wubi? Then can you back up your data - /home and anything else you want and delete wubi from windows. Then you should have more room for a full install.

Is there any other housecleaning you can do in windows? When windows/NTFS gets to about 10% free it slows down a lot and you just about cannot run a defrag as there is no working room to move data about.

---

### Post by Bucky Ball on 2011-01-03
Yep, backup Wubi personal data, defrag once more, try again. ;)

---

### Post by mick222 on 2011-01-03
How big is your hard drive.

---

### Post by mike555 on 2011-01-03
You do know that you can't partition a hard drive that is running,right?    you will need to use a live cd with gparted to do it ......
   well , never mind , I reread your post and see your on the right track......

---

### Post by camtom12 on 2011-01-03
HD is small, it's a 5-6 year old laptop that's been a stand-in since my nice 2009 model found a puddle on top of it.  I think it's 80GB with at least 10GB full of recovery stuff.  I think it's call Sony Diagnostics or somesuch.

I've got a pretty small Wubi I think.  I really don't have anything saved under that OS yet as I just wanted to give it a shot and knew I'd do a real install before I used it seriously.  Unless the Wubi itself is big.  In that case oh well.  I'll be getting a new Acer in a little bit so I'll just wait on a real install until then.

Thanks for all the help and suggestions!

Moderators can mark this as Solved if you'd like!

---

