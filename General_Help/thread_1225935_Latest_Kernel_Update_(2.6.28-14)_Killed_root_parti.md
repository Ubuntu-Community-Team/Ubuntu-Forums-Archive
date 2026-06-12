---
title: "Latest Kernel Update (2.6.28-14) Killed root partition"
date: 2009-07-29
forum: General Help
---

### Post by PureLoneWolf on 2009-07-29
Hi there

I am desperate for help right now.  I woke up this morning and noticed that my girlfriends laptop had some updates waiting, one of which was the new kernel version.  As I had performed a re-installation and data restore yesterday, I let it run through.

Only to be presented with a Grub Error 17 message.  I booted from the Live CD and according to Gparted, the 20gb root partition is unallocated.

Can someone help me get this back please.

Her laptop is running Jaunty and I am writing this from the Live CD.

Thanks

**EDIT**

I should add that the laptop is purely ext3, there is no dual boot anywhere.

---

### Post by nepmak2000 on 2009-07-30
I was recently fighting the same grave problem! The solution was simple: make use of the originally install ...28-11, anyway NOT 28-14 kernel in the GRUB.
What I did?
Use the LiveCD. Terminal: gksudo nautilus  In Nautilus now (as root) find the Filesystem on the Laptop. Open the Filesystem and find 'Boot'->'Grub'-> menu.lst.
Open the menu.lst in Gedit (text editor). Then do see below the middle where the 'magic' is mentioned the series of installed Kernels. The first 2 entries will most likely be the .28-14 kernel and nextly another 2 entries for the 28.11 kernel.
You guess it already: edit the 14's (take care there are 3 in each entry group) into 11 and for the sake of change the 11 to 14. Then bravely reboot. That should work like a clock!
I am studying the peculiar phenomenon in Kernel 28-14, which seems to me having to do with EXT4 formats clobbering the EXT3 inode bit trains and then you're completely lost!
All the best. The problem is minimal, the consequences however dire (at first sight!).
:(

---

### Post by PureLoneWolf on 2009-07-30
I tried various grub fixes..the problem was that it was unable to access the / partition at all to be able to get there.

In the end I re-installed - Fortunately Ubuntu doesn't take long to get back to full strength :)

---

