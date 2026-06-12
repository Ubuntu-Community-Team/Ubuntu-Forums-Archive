---
title: "Swap File and Disk Free Space"
date: 2009-08-19
forum: General Help
---

### Post by alindgr1 on 2009-08-19
In windows, I heard it was "good" to keep at least 50% free disk space.  I assumed that this is because of the swap file being stored in the same space that everything else normally is.  Now that I have Ubuntu, I know that the swap is on a different partition, so I would assume that this is not the case.  My question is this:  is it OK to fill the Ubuntu partition up to nearly 100%?  This is not a goal, and I am not even close to this, but I am just curious.

---

### Post by Psycho.mario on 2009-08-19
You can fill it to 100%(Well 99.999999....%). You may see a drop in performance when finding files though.

---

### Post by alindgr1 on 2009-08-19
Thanks for the info.  I will keep that in mind, and perhaps use it when discussing the perks of Ubuntu and GNU/Linux is general.

---

### Post by anaconda on 2009-08-19
atleast with default ubuntu install with ext3 a whopping 5% of your disk is (was?) reserved for root user, so if the disk fills up you could log in to a recovery mode (as root) and then you would have enough room to correct the problem.

Actually 100MB would be more than enough for this purpose, and the ubuntus default 5% !! is absolutely ridiculous with normal >500GB disks. And even then the 100MB would only be needed in the root partition.

This is one reason I usually install ubuntu using the alternate install cd. With alternate Cd you can choose how much room you want to reserve for root user.

By the vay. even if the disk is completely filled the swap file(or partition) wont be overwritten. they are permanently reserved for swap use. (actually now it IS possible to have a swap file, that changes size if/when needed, but I have never tiried it.)

---

