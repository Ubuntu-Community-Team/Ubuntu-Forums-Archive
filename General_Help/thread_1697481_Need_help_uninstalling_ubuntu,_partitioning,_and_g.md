---
title: "Need help uninstalling ubuntu, partitioning, and grub."
date: 2011-02-28
forum: General Help
---

### Post by asoccer345 on 2011-02-28
I tried to dual-boot ubuntu and vista. I worked well, I guess, but something went wrong, and now I want to uninstall it. I may reinstall it later. I am using Meerkat 10.10. I have no idea really how to get my computer back to normal with no Ubuntu and grub. I need someone to write the instructions step by step, easy, so I can write it down and do this. Please help, I need it back also because now I only have 215 mb of space on my windows partition, so no downloads would be nice.

---

### Post by amjain on 2011-02-28
Ok there are several ways to do this. (I myself did this couple of times few months back).
But let me suggest you some thing - It will be great if you have access to another computer with internet, in case some thing goes wrong.

Now for the solution:

Do you have your dual boot working now. I assume yes. From Grub there fore you can choose to go to windows. 
If yes, then you can very well delete the linux partition (assuming you have backed up yr data).
Once you have deleted the linux partition, you can always extend the windows over this new space. 

We will un-install grub later. First you sync up to this step.

---

### Post by asoccer345 on 2011-02-28
Ok, how do I delete the linux partition?

---

### Post by amjain on 2011-02-28
I am assuming you partitioned your hard disk to create separate partition for ubuntu from Windows. 
Basically boot into windows. Run your parition tool again (partition magic or whatever tool you used).

You can always use fdisk from windows command prompt. 

Check these links [http://www.computerhope.com/issues/ch000344.htm](http://www.computerhope.com/issues/ch000344.htm)

Once your ubuntu is deleted, deleting grub is possibly by fdisk /MBR

[http://www.computerhope.com/issues/ch000175.htm](http://www.computerhope.com/issues/ch000175.htm)

---

### Post by asoccer345 on 2011-02-28
Actually, I made the partition during the Ubuntu installation,but I guess it's the same? Anyway, I heard that the people on Ubuntu forums. Are very helpful, and this has been true. Thank you! I may need some help tomorrow when I try this though.

---

### Post by Hedgehog1 on 2011-02-28
> **amjain said:**
> I am assuming you partitioned your hard disk to create separate partition for ubuntu from Windows. 
Basically boot into windows. Run your parition tool again (partition magic or whatever tool you used).

You can always use fdisk from windows command prompt. 

Check these links [http://www.computerhope.com/issues/ch000344.htm](http://www.computerhope.com/issues/ch000344.htm)

Once your ubuntu is deleted, deleting grub is possibly by fdisk /MBR

[http://www.computerhope.com/issues/ch000175.htm](http://www.computerhope.com/issues/ch000175.htm)

May I please suggest changing the order of these two tasks?

Do the FIXMBR fist (so the PC can always boot) and then remove the unwanted partitions with whatever tool you suggest?

Otherwise the OP can end up with a non-booting PC for a while.

***The Hedge***

:KS

---

### Post by asoccer345 on 2011-03-02
So, do fix MBR first? Is that the best option?

---

