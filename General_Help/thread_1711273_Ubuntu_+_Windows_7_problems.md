---
title: "Ubuntu + Windows 7 problems"
date: 2011-03-21
forum: General Help
---

### Post by Zio_Pecos on 2011-03-21
Hello everyone, this is my first post.

I've tried looking into the forum for cases similar to mine and I did'nt find any, so here I am

This is my problem
on my 500Gb hd I had Win7 64

I installed Ubuntu 10.10 repartitioning from the live cd giving half to each o.s.

Since I wanted to get rid of Win7, leaving to it just a little space, I moved all the personal and work data from one partition to the other (using ubuntu). in this way I cleared a lot of space and I wanted to repartion and give this free space do ubuntu.

At this stage stil both o.s. were working.

I guess I messed up with Gparted live cd and now Win7 is not loading anymore...it is even not present in the grub's list...

Moreover i tried to fix it using the win7 cd but I ended up with my laptop not booting anymore.
In the end in order to solve this problem I used the ubuntu live cd and I installed on a little partition again ubuntu...

In this way I'm able to boot and through grub I can select the old partion were ubuntu had been installed.

What can I do to remove the partion I had to create to make my laptop boot?

Moreover once I do that, how can I restore into the the grub the dual boot?

guys I look forward to hearing from you.

---

### Post by zvacet on 2011-03-21
With Ubuntu live CD and gparted program remove partition you made and extend Ubuntu partition(if you shrinked Ubuntu partition to made new one).That way you should have only two partitions,Windows and Ubuntu.Reinstall grub following [this]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") guide.

---

### Post by tyleruk on 2011-03-21
Personly I would copy the data you want to keep to a USB HDD then wipe the whole drive and re-install from sctratch.

At least that way you can get a nice clean install.

---

### Post by 3Miro on 2011-03-21
What happened is:
1. When you moved the windows/Ubuntu partitions, something went wrong and windows possibly got damaged. You could have tried "sudo update-grub", but maybe it wouldn't have worked. It is alway recommended to make a full backup before you mess with partitions.

2. Windows doesn't play with other OS. The Windows mentality is that you will only have windows and nothing other than windows. Hence, windows repairs always damage Ubuntu.

zvacet's solution will work. Remove the new Ubuntu partition and then reinstall Ubuntu Grub. This will give you back your Ubuntu. However, you will not get windows back.

tyleruk's solution is better in my opinion. Since things have gone wrong before, I wouldn't do repartitioning again unless I have backed up everything. See if you can get an external HDD (either buy one or borrow one). Once you have everything backed up, you might as well reinstall/repartition everything. You can also put windows back (if you want), but make sure to install it before Ubuntu.

---

### Post by Mark Phelps on 2011-03-21
> **Zio_Pecos said:**
> At this stage stil both o.s. were working.
So, both Ubuntu and Win7 were working AFTER the dual-boot install?

> I guess I messed up with Gparted live cd and now Win7 is not loading anymore...it is even not present in the grub's list...
That often happens if you resize Windown partitions using Linux utilities.

> Moreover i tried to fix it using the win7 cd but I ended up with my laptop not booting anymore.
You often have to run Startup Repair three times to get booting working again.

---

