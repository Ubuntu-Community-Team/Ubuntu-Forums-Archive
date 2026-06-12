---
title: "Setting up RAID with existing data"
date: 2009-12-05
forum: General Help
---

### Post by directedition on 2009-12-05
Hello,

I have a 1.5TB drive filled to the brim with data, and I'm worried having a failure and losing it all, so I'm buying another drive and looking into setting up a RAID 1 array.

All the tutorials I come across start off with blank discs, but I don't have anywhere to put my data while I'm setting up the discs. Is there a way to setup RAID with a disc that already has data on it?

---

### Post by fluffman86 on 2009-12-05
RAID 1 is just mirroring, so it won't give you any more space.  If it were me, and that 1.5 TB was chock full and I didn't change it a whole lot, then I would put the unchanging bit--the old stuff--on a new 1.5TB drive and throw it in a safe deposit box or a relative's house or somewhere off-site to keep it *REALLY* safe.  The stuff that changes more could stay in your /home dir and mirror on a smaller drive.

All of that said, my workings with RAID 1, which are indeed limited, have led me to believe that they pretty much start mirroring straight away.  So if you use the raid tools and make a new array, and add first add your current disk, then add your blank disk as a secondary piece to the array, then all of the data should sync over immediately.

---

### Post by whoop on 2009-12-05
Maybe this thread will help you:
[http://ubuntuforums.org/showthread.php?t=1165328](http://ubuntuforums.org/showthread.php?t=1165328)
Especially the last posts in the thread...

---

