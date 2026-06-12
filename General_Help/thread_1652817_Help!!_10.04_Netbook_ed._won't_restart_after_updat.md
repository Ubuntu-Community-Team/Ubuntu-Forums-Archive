---
title: "Help!! 10.04 Netbook ed. won't restart after update"
date: 2010-12-25
forum: General Help
---

### Post by JEBB on 2010-12-25
I use my DM9 with Ubuntu 10.04 for my traveling computer and I am traveling.  I made the mistake of letting it run updates and now it won't restart.  It stops at this message at start up: (initramfs)

It has lots of information associated with my trip.  How do I proceed from here to get it working??

Thanks.

---

### Post by lsmobrian on 2010-12-25
Have you tried to see if booting into a previous kernel helps?  When you start the computer hold shift, the grub menu should come up, select the next kernel version down

Or does it not even load grub?

---

### Post by JEBB on 2010-12-25
Thanks for your reply...

I have now tried the next two down and always get the message: "No init found.  Try passing init= bootarg".   Followed by the message (initramfs).

---

### Post by lsmobrian on 2010-12-25
You dont by chance have a USB with the install disk or liveCD do you?

Boot into that, and get to a terminal and run 
```
fsck -y /dev/sdaX
```
Where X is your root partion, most likely sda1.  And you may need to use sudo.  If you're unsure, you can run this and you should see a * under the boot column for one partition
```
sfdisk -l
```

---

### Post by JEBB on 2010-12-25
I was able to borrow a PC and make a GParted live USB and start from there.  I put in the commands you suggested and it worked!  

Can you tell me what went wrong with the update and how I can avoid that the next time?

---

### Post by lsmobrian on 2010-12-25
My best guess, it went to sleep/hibernate mid upgrade and something got messed up due to that... but I really have no clue.  It looks like maybe the long id, UUID, for the partition (/dev/disk/by-uuid/) gets out of sync or gets the wrong value and grub can no longer find the partition to boot from.

I've never had it happen to me, but just in case of anything, I do always keep a thumb drive setup with the install disk with my netbook.

Sorry I cant be more helpful with the 'why did this happen' but I'm glad you got your system back semi-painlessly

---

