---
title: "Ubuntu Unistalled But Memory Space Not Returned"
date: 2009-12-02
forum: General Help
---

### Post by jforjustin on 2009-12-02
I don't know what's happened, but I'm now missing 10gb of my hard drive's memory.
 
I installed ubuntu using wubi (?) because I didn't want to partition my hard drive.
 
Ubuntu completely froze and wouldn't respond, so I restarted my computer. I then realised Ubuntu wouldn't boot. I realised in Windows, that C:\Ubuntu\Disk\ (or something) was corrupt, so windows did a disk check and removed the file (Since I couldn't even delete or access it).
 
Anyway, I then unistalled ubuntu after the disk check, but the 10gb of data I selcted to be used for ubuntu is still missing.
 
Any ideas...?

---

### Post by oOarthurOo on 2009-12-02
IIRC Windows doesn't delete corrupted files when repairing disks, it puts them somewhere safe where you can look into further.

Open 'My Computer', right-click on your 'C' drive, and choose search. Search for the following files:

*.tmp,*.chk,~*.* 

Be sure to check the box that says search for hidden files and folders. Delete everything that is found. Empty your recycle bin.

You should have your space back now.

---

### Post by claracc on 2009-12-02
You have to look for a hide folder in c:\, i think its name is .1000  or something similar, then you delete it and you recover your lost space.
I hope it can help

---

