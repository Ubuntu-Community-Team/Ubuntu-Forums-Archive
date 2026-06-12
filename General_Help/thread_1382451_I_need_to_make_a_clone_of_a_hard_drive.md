---
title: "I need to make a clone of a hard drive"
date: 2010-01-16
forum: General Help
---

### Post by rainbowagent7 on 2010-01-16
Thanks in advance to anyone who can help. I'm new to Ubuntu, and still getting the hang of it. I have two 40 GB ATA hard drives, I recently installed the second one to use as an identical clone in case anything should go awry, to back up data on a daily basis exactly as it is written on the first one. However, I've never done file transfer before and this is all new to me. I know there is more than likely some kind of file transfer wizard or an easy process for this. Any help would be greatly appreciated as school is coming up soon, and I need some kind of backup plan.

---

### Post by JackRock on 2010-01-16
If you want the backup to be done on an incremental basis (not simultaneously), then I suggest a third-party backup software.  There are many available, just do a search.  I have none to recommend, however.

If you're concerned about HDD physical failure, you could simply set up a RAID1 configuration.  But it wouldn't protect against software failure - only hard drive physical failure.

---

### Post by rainbowagent7 on 2010-01-16
Thanks for the reply. Actually I didn't even know that it could be backed up simultaneously, that's exactly what I need. What steps do I need to set that up? Do you need any system info from me?

---

### Post by JBAlaska on 2010-01-16
Try the [Clonezilla LiveCD](http://clonezilla.org/) that should do the trick for you.

You can also copy partitions with gparted on the Ubuntu Live CD, But I think Clonezilla is a better solution for a 1:1 clone

---

### Post by rainbowagent7 on 2010-01-16
I'll give them a try, thanks again for all your help. Also thanks to everyone else out there for all of your hard work!

---

### Post by warfacegod on 2010-01-16
This might be worth your time as well:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by Sef on 2010-01-16
> Try the [Clonezilla LiveCD]("http://clonezilla.org/") that should do the trick for you.

+1.  There is tutorial on the Clonezilla site that shows you how to clone your hard drive.

---

### Post by stormbay on 2010-01-16
What about "Parted magic" which has taken over from clonezilla I beleive.

I use "remastersys" but I also run Open Suse in another partiton and no remastersys for that. They have "kiwi" which I can't get loaded let alone figure it out. So I've downloaded "parted magic" which include a rescue section a heaps more and will check it put tonight an let yo know how t goes. I like the idea of live CD solutions for things like this, it means you can operate outside the system.

---

