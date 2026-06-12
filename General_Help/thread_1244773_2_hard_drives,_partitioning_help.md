---
title: "2 hard drives, partitioning help"
date: 2009-08-19
forum: General Help
---

### Post by Thy_king on 2009-08-19
Hey guys, still pretty new with ubuntu 9.04 64bit

I've got a question regarding partitioning.

Right now i have ubuntu installed on a 80GB hard drive.
I had windows installed on a 250GB HD with different partitions.

I want to get ride of windows completly which means that i want to get ride of the ntfs partitions and have an 80GB and 250GB all for Ubuntu.


Can I partition both drives so that the second partition is within my /home directory or will i always see a second drive on  /Computer?
Is it worth switching to ext.4?

If i can do it, what would be the best way to partition both drives.
I don't mind re-installing ubuntu if i have to, as i backed everything up already.

Your help would be greatly appreciated.

Thanks

---

### Post by SoftwareExplorer on 2009-08-20
I'm assuming you meant git rid of windows. I would say its possible to have the second partition on /home, but I think you would have to make the second partition ext3 or some other Linux filesystem, I don't think /home on ntfs works. (I could be wrong, though)

---

### Post by Megrimn on 2009-08-20
'/Computer' displays the different disk drives that are attached to your computer.  Optical Drives and Floppy Drives are always displayed, whether or not there is any media in them.  Hard Disks, however, are displayed by partition.  Take my HDD, for example.  As I am dual-booting Ubuntu and Vista, there are 3 partitions that show up:Windows recovery, Vista, and Ubuntu(filesystem).  But they are all on the same HDD.  If I were to delete the Vista partition, it would no longer show up on /Computer, since there is no filesystem where the partition was.  

/Computer will always display the partitions on disks you have plugged into your computer, provided they function properly.  What I suggest you do is reformat the 250G HDD (provided you really do want to get rid of windows) with the liveCD.  It has a program called 'partition editor' under the system -> administration menu, which you can use to delete partitions, create partitions, edit partition size, and copy a partition to another location, like another HDD.

I have no experience with ext4, so I have no idea what the drawbacks or positives are about that filesystem at this time.

and as for making a directory for the one HDD in the home directory, it's physically impossible, since you would either be copying the other HDD's contents to it or would have to physically implant the HDD space into the other. 

BUT it is possible to make a *shortcut* that directs you to anything on the other HDD.  I think Ubuntu would even automatically mount the other HDD if you clicked on the shortcut.  Just make sure the other HDD is physically attatched to your computer.

Happy Partitioning.

---

### Post by SoftwareExplorer on 2009-08-20
[LEFT]I have heard of ext4 loosing data if the computer looses power while doing lots of stuff, but that may be fixed by now. What I usually do is have ubuntu installed on ext4 for faster booting and /home on ext3 for data safety. If you loose ubuntu, then you just have to reinstall and reinstall programs, all your user data in /home is still there with how I do it. 
[/LEFT]

---

### Post by Thy_king on 2009-08-20
Ok, thanks guys,

I guess the easiest thing for me right now would be to just leave it as is until i absolutly need to repartition and format my NTFS drives.

Thanks for your input, it's greatly appreciated.

---

