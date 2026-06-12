---
title: "how come I can't increase partition size using gparted"
date: 2011-04-01
forum: General Help
---

### Post by keevill on 2011-04-01
I have a dual boot machine ( win 7 & Ubuntu 10.04 ) which is reporting insufficient space on the Linux partition.
I boot up into gparted and reduce the size of the the preceding partition but when I try to increase the size of the following ( linux ) partition, it won't allow it.
Attached is a screenshot of the gparted info screen.
Please can someone help .
Thx,
-keevill-

---

### Post by wojox on 2011-04-01
Your using a Live-CD correct. Also I don't see any free space to expand it with.

---

### Post by oldfred on 2011-04-02
If you are going to shrink sda4 you have to do that first. Then you have to move extended partition left into the new free space. Then you can move sda5 left & expand it. This is a lot of moving since all data in sda5 will have to be copied left.

Make sure you have good backups. 

What you are doing should not change any partition numbers or UUIDs, but moving the start of the Linux partition may require you to reinstall grub's bootloader to the MBR. 

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ApocryphalAuthor on 2011-04-02
First, props for a literal screen shot. :D

So it looks like you are trying to make /dev/sda5 bigger, and to do this you reduced /dev/sda2 (the Windows 7 partition.)  Am I correct? 

When you shrink /dev/sda2 from the right, the space is added to /dev/sda4 (the next partition to the left) if it allocated at all.  To get that space to /dev/sda5, you're going to need to shrink /dev/sda4 from the right and have it allocated to /dev/sda3 (the extended partition that /dev/sda5 lives on.)  Then you'll be able to grow /dev/sda5 appropriately.

Let us know how it goes for you.

---

### Post by keevill on 2011-04-02
> **ApocryphalAuthor said:**
> First, props for a literal screen shot. :D

yeah ! I tried twice to use the gparted screenshot but I couldn't find gparted.jpg in the home/users !! 
:-)


So it looks like you are trying to make /dev/sda5 bigger, and to do this you reduced /dev/sda2 (the Windows 7 partition.)  Am I correct? 
Yes !

When you shrink /dev/sda2 from the right, the space is added to /dev/sda4 (the next partition to the left) if it allocated at all.  To get that space to /dev/sda5, you're going to need to shrink /dev/sda4 from the right
OK, I did that but the next bit confuses me.

 and have it allocated to /dev/sda3 (the extended partition that /dev/sda5 lives on.) 

How do I do that ?

 Then you'll be able to grow /dev/sda5 appropriately.

Presumably, I am gonna lose the grub and have to re-install it ?
How likely is it that I am going to screw up the Ubuntu installation ?


Let us know how it goes for you.

Thx !
-keevill-

---

### Post by Mark Phelps on 2011-04-02
If I understand what you want to do is shrink sda4 and expand the partition on the right into that space, right?

To do that, you would have to to the following in order:
1) shrink sda4 -- leaving space on the right
2) expand the Extended partition -- to the left -- to take up the new unallocated space
3) expand the partition inside the Extended partition to the left.

---

### Post by keevill on 2011-04-03
> **Mark Phelps said:**
> If I understand what you want to do is shrink sda4 and expand the partition on the right into that space, right?

To do that, you would have to to the following in order:
1) shrink sda4 -- leaving space on the right
2) expand the Extended partition -- to the left -- to take up the new unallocated space
3) expand the partition inside the Extended partition to the left.

Thx everyone ! It went off without a hitch - no need even to reinstall grub !!
-keevill-

---

