---
title: "Help creating RAID 1 backup"
date: 2010-06-27
forum: General Help
---

### Post by hoffmaster on 2010-06-27
I have been searching for a way to create a RAID 1 array using 3 partitions on 3 different drives.  I have found lots of information on how to install Ubuntu with Raid, but nothing that can help me after I have installed already.

So here are the detail of what I want:

I want to have a 20GB partition on 3 different drives.  I would like to have a RAID 1 array (I think that's the one where I would get 3 mirrors).  I would like to have the RAID 1 array auto mount.

If possible I would like to make it so that it was shared to allow read, and file adding, but not file deleting or modifying.  I am sure there is a tutorial on how to do all this already.  But I am very new to linux and am still having trouble finding the information I need. 

I am using Ubuntu 10.4 desktop.

---

### Post by hoffmaster on 2010-07-01
Alright this is actually pretty easy...

1. In Ubuntu open up the Disk Utility.  
2. Go to File->Create->Raid Array.
3. Pick hard drives that have free, non-partitioned space.
4. Choose your raid array size and create.
5. If you get an error you need to install mdadm, I did this through the software manager in ubutnu.
6. Whablamo done.

---

