---
title: "Resize ubuntu partition?"
date: 2010-11-27
forum: General Help
---

### Post by dbunder on 2010-11-27
I've looked everywhere for a definitive answer to this, but haven't found one.  Lots of roundabout discussions and "I dunno."

I installed ubuntu jaunty (i'm up to maverick) on my laptop forever ago on a 40gb partition with the Win7 beta on the other partition.  I haven't used Win7 since I installed, so I want to take over the whole disk.

The Win7 partition(s) are at the beginning of the disk, and the ubuntu partitions are at the end of it.  Is there any way to grow my ext3 partition to take over the whole disk without losing anything?

Have a really good dev environment/print-/fileserver set up and it wouldn't be terribly fun to set up again.

---

### Post by NertSkull on 2010-11-27
I've never done it, so I can't say for sure.  But I'm pretty sure I've read about people doing it, so I think it can be done relatively easily.

Anyway, I'm pretty sure you can just use gparted to do it.  Find it in the repositories.  Its WAY easy to use.  

Read up on that and I suspect you'll have your answer, I suspect if you just want to get rid of windows you won't really even have to mess with the bootloader.

BUT. Make 100% SURE that you backup anything you need before you ever mess with partitions.

p.s. Check out duplicity for an awesome backup solution

---

### Post by Spyderkid on 2010-11-27
Can't you go to....

System> Administration> GParted Partition Editor

---

### Post by dandnsmith on 2010-11-27
For peace of mind, backup the current Ubuntu partition.

Then boot from somewhere which isn't the Ubuntu partition into gparted - you really don't want to try to operate on the currently live partition (and I think gparted won't let you).

On the whole gparted itself will let you know what operations are feasible (and will probably prompt you to think about backup)

---

### Post by dbunder on 2010-11-27
I'll give it a shot when I have a little time.

gparted is a great tool, but I've heard that it won't expand partitions unless you're expanding the end of the partition, and in this case I'd be appending to the beginning of it.  Haven't been able to get a straight answer on whether that's true or not.  Doesn't say anywhere in the docs.  I'll boot into it and see if it'll even let me do that operation.

Thanks for the duplicity suggestion.  Looks nice. :)

---

### Post by Herman on 2010-11-27
GParted has had the ability to 'move' the start point of partitions containing Linux file systems very quite a long time now, however it is an exceedingly slow process. It is useful is some circumstances though, like when your Ubuntu installation is more than half the size of your hard drive and also contains a lot of files.

You should have backup copies of all your files on some other media before using any partition editor, of course.

If your Ubuntu installation occupies less than half of your hard disk it will probably be a lot faster to use GParted's copy and paste features instead.
Just delete the Windows partitions and copy and paste the entire Ubuntu partition to the empty space at the start of  the disk. Then delete the original Ubuntu partition and resize the new copy to  the right to fill the disk. The right-hand end of the partition is a lot faster to expand from.

---

### Post by oldfred on 2010-11-27
I do not like moving partitions left as it requires everything to be copied & verified. Slow and slightly more risk than other partition edits. If should not change UUID with just a move but if it does you have to change fstab. You may have to reinstall grub.

Another alternative is just to make the partition a data partition and mount it into your system.

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by Herman on 2010-11-27
> If should not change UUID with just a move but if it does you have to change fstab. You may have to reinstall grub.GParted changes the UUID of the old file system instead, and retains the original UUID in the new copy, or at least it did when I last tested it for that. So it's about as close as can be to being trouble free. :)

---

### Post by dbunder on 2010-11-27
> **Herman said:**
> GParted has had the ability to 'move' the start point of partitions containing Linux file systems very quite a long time now, however it is an exceedingly slow process. It is useful is some circumstances though, like when your Ubuntu installation is more than half the size of your hard drive and also contains a lot of files.

You should have backup copies of all your files on some other media before using any partition editor, of course.

If your Ubuntu installation occupies less than half of your hard disk it will probably be a lot faster to use GParted's copy and paste features instead.
Just delete the Windows partitions and copy and paste the entire Ubuntu partition to the empty space at the start of  the disk. Then delete the original Ubuntu partition and resize the new copy to  the right to fill the disk. The right-hand end of the partition is a lot faster to expand from.

Perfect!  That sounds pretty straightforward.  As soon as I take a disk image of my ubuntu install I'll give it a shot and see what happens. 

Thanks a ton for the help everybody!

---

