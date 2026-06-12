---
title: "GParted question"
date: 2011-11-09
forum: General Help
---

### Post by crutch145 on 2011-11-09
My Ubuntu partition resides on a partition of 190.73 GiB.  I have 74.33 GiB of unallocated space.  How can I combine the 74.33 GiB with my 190.73 GiB to make one single partition?  

Thanks,

Justin

---

### Post by aeiah on 2011-11-09
using a livecd, you should be able to increase the size of your ubuntu partition into the unallocated space.

if the unallocated space is before the ubuntu partition (ie, to the left of it in gparted) then i think gparted will move the partition. this carries a risk. either way, you should probably back up important data.

---

### Post by Matti L on 2011-11-09
If you boot from the Live CD or USB you can resize your Ubuntu partition. Might want to backup first though.

EDIT: aeiah already answerred. Nevermind me then.

---

### Post by Foxheadz on 2011-11-09
Your gonna have to boot into a Ubuntu Live CD and then from there unmount your hard drive and expand your ubuntu partition to take up the extra space.

---

### Post by crutch145 on 2011-11-09
I am in live cd now and have gparted open.  when i highlight the partition i want to increase, and select Resize/Move, it will not let me increase the size.  i can see my unallocated space (to the right of my ubuntu partition.  there is windows partition between them.  is that what is causing the problem?

---

### Post by fantab on 2011-11-09
Can you post a Screen Shot of the Partition Scheme?

If you have a partition in between unallocated space and where you want to add that space to then, I am afraid you cannot do that easily without endangering the data in between.

You may have to reconsider your Partitioning Scheme which may force you to reinstall. 

I strongly suggest that you BACK UP all important DATA and only then proceed.

---

### Post by oldfred on 2011-11-09
Yes.

You may be able to move the Windows partition, but that will create many issues. The boot sector of a NTFS partition has to match the partition table. Moving it does not update the boot sector and you have to do Windows repairs of fixBoot and chkdsk. Much more risk, so have very good backups.

Depending on what is where you may be able to do something else. I normally suggest Ubuntu / (root) partition be only 10-20GB and use another partition for /home or for data. If dual booting with Windows you should have a NTFS shared partition for data anyway. I share my Firefox & Thunderbird profiles in a NTFS partition and have the same Firefox & Thunderbird in both systems.

---

### Post by crutch145 on 2011-11-10
Thank you all for this information.  I have decided the best route is to re-install Windows first, then Ubuntu.  I should not have allocated so much space to Windows the first time around... since I am primarily using Ubuntu for everything.

---

