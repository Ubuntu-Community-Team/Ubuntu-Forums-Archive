---
title: "Stealing space from Windows partition"
date: 2010-08-05
forum: General Help
---

### Post by AgungBebek on 2010-08-05
Anyone know, how to steal space from a Windows partition and transfer it to my Ubuntu partition?

---

### Post by dv3500ea on 2010-08-05
Boot from the live CD and use the partition manager (gparted).

You will need to shrink the Windows partition and move/expand the ubuntu partition.

Make sure you back up important files first.

---

### Post by oldfred on 2010-08-05
If it is Win7 or Vista then it is better to use the window tools to shrink the windows partition. You do have to use gparted with XP.

Depending on where your partitions are it may be a big task to move everything around. If you want you can just make a new partition and use it for /home or a /data.

---

### Post by mojo risin on 2010-08-05
> **dv3500ea said:**
> Boot from the live CD and use the partition manager (gparted).

You will need to shrink the Windows partition and move/expand the ubuntu partition.

Make sure you back up important files first.
How could I do this without a working optical drive?

---

### Post by oldfred on 2010-08-05
Can you boot from a USB? If not plan on a new CD drive.

---

### Post by mojo risin on 2010-08-05
I guess I will need a new cd drive then.(I have seen so many things which require a working optical drive. I might just need to get a new drive, or find a way to fix it (whatever has a higher possibility)

---

### Post by oldfred on 2010-08-05
Sometimes a good cleaning. The lens can get covered with dust. Are all the connections tight? Does it spin, when you insert a disk?

I really like using flash now and try to convert as much as possible to flash drives. They are reusable and larger, so you can do multiple things with them. There are ways to get flash to boot from a floppy or the CD.

---

### Post by AgungBebek on 2010-08-07
I  cannot find any partion tools in Windows Vista. Also, I installed Ubuntu by internet, so ...

Thanks, anyway :-)

---

### Post by Mark Phelps on 2010-08-07
> **AgungBebek said:**
> I  cannot find any partion tools in Windows Vista. Also, I installed Ubuntu by internet, so ...

Thanks, anyway :-)

Well ... you're not looking very far ...

Use the Disk Management utility.  Type "Disk Managment" in the start area, it should offer to open the msc app for that.  Use that to work with partitions in Vista.

BTW, if you go to the GParted website and read through the FAQs there, you will find one dealing with installing Goarted to the hard drive.  If you follow their instructions, they also include lines you can add to a GRUB3 Custom file, such that, when you regenerated the GRUB menu, you will have an entry for GParted -- which you can then boot into.

However,  do NOT use GParted for messing around with Vista partitions.  Doing so runs the risk of corrupting the Vista OS partition and rendering it unbootable.

---

### Post by AgungBebek on 2010-08-08
> **Mark Phelps said:**
> Well ... you're not looking very far ...

Use the Disk Management utility.  Type "Disk Managment" in the start area, it should offer to open the msc app for that.  Use that to work with partitions in Vista.

BTW, if you go to the GParted website and read through the FAQs there, you will find one dealing with installing Goarted to the hard drive.  If you follow their instructions, they also include lines you can add to a GRUB3 Custom file, such that, when you regenerated the GRUB menu, you will have an entry for GParted -- which you can then boot into.

However,  do NOT use GParted for messing around with Vista partitions.  Doing so runs the risk of corrupting the Vista OS partition and rendering it unbootable.
Maybe not far enough, but certainly far. :-)

However, I'm a complete idiot with respect to MicroShit products. I'm soo old, that I still prefer a prompt and the "tab-key" and do my programming in f77 ;-)

I'll give it another try. Thanks

---

### Post by AgungBebek on 2010-08-09
> **AgungBebek said:**
> Maybe not far enough, but certainly far. :-)

However, I'm a complete idiot with respect to MicroShit products. I'm soo old, that I still prefer a prompt and the "tab-key" and do my programming in f77 ;-)

I'll give it another try. Thanks
No, I looked far enough: The only disk management tools on my Vista is "defrag" and "clean-up"

---

### Post by oldfred on 2010-08-09
I only have XP but found this:

[http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista](http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista)

The folks at Redmond were kind enough to include a disk partitioning  tool in Vista if you know where to look. So go to Control Panel ->  System and Maintainence (skip this one if you're in Classic view) ->  Administrative Tools -> Computer Management. Once you launch the  Computer Management tool, click on Disk Management under the Storage  heading in the sidebar. It's partitioning time.

---

### Post by Mark Phelps on 2010-08-09
> **AgungBebek said:**
> No, I looked far enough: The only disk management tools on my Vista is "defrag" and "clean-up"

Did you type "Disk Management" in the start area?  OR did you just look through the menu entries in All Programs?

If the latter, it's really hard to find that way.

Anyway ... oldfred gave you the path to the Disk Management utility.

---

### Post by AgungBebek on 2010-08-10
I did as you suggested

I also did as Oldfred suggested, but the screen tells me that there's no available space.

The reason is, I believe, that my hard drive is divided between Vista  and Ubuntu, which is why I want to shrink the current Vista partition. 

So, I guess the only way is to save all my files on an external drive and then repartion the entire hard disk :-(

Thanks for your help.

---

### Post by mojo risin on 2010-08-14
> **oldfred said:**
> Sometimes a good cleaning. The lens can get covered with dust. Are all the connections tight? Does it spin, when you insert a disk?

I really like using flash now and try to convert as much as possible to flash drives. They are reusable and larger, so you can do multiple things with them. There are ways to get flash to boot from a floppy or the CD.
I know in windows it spins a couple of times and shows the CD icon but thats it nothing else happens. no problem with drivers though. I also tried to burn sth and it actually sometimes recognised a cd , but that wasnt often and about a few seconds after starting it would lose the recognition again.

---

