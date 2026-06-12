---
title: "Will I need to chain boot?"
date: 2011-10-08
forum: General Help
---

### Post by ClientAlive on 2011-10-08
I'll be creating another system on my hard drive tonight (a second/ other computer) but it already has Windows xp on the 2nd partition and I have to have that to do tests for one of my classes. I will be using grub 2 for my boot loader (of course) and am wondering if I will need to set it up to chain boot the windows partition in order for it to still boot.

My 2 concerns (and they're kinda connected) are:

1) I have that windows install because I have to have it for school, for doing tests for one class and accessing a vm for another. And - I can't afford it to be down for very long or for something to happen where I can't get my work in on time.

2) I'm not sure how much of this build I can accomplish tonight but I'm gonna get as far as I can. If I end up somewhere in the middle and have to do a test or access the vm - I need to have some idea how to ensure I can boot windows while make these other changes/ build.


Any ideas?

:)

---

### Post by Quackers on 2011-10-08
As long as nothing is wrong with XP then grub will boot it if it's installed to the mbr of the drive.

---

### Post by Dareth on 2011-10-08
Quackers is completely correct. If your XP partition is healthy, Grub will detect it and create a menu item for it.

---

### Post by ClientAlive on 2011-10-08
> **Quackers said:**
> As long as nothing is wrong with XP then grub will boot it if it's installed to the mbr of the drive.

So grub will just automatically recognize it? Or I have to go edit my fstab file and add that Windows partition? I'll be building this other system from scratch so maybe not the same as when you have an installer doing everything for you?


Thanks
-------------

Edit:

I thought the mbr was a Windows specific thing and would currently be on that partition where Windows is.

---

### Post by ClientAlive on 2011-10-08
> **Dareth said:**
> Quackers is completely correct. If your XP partition is healthy, Grub will detect it and create a menu item for it.

Oh cool! I hope it all goes that smoothly.
-----------------

Edit:

So, if I'm not mistaken about the mbr thing being Windows specific. And, if I'm not mistaken about it currently being on that partition where Windows is - then does grub just take the place of the mbr? Supersede it so to say? In the end grub just boots Windows and the mbr is not involved?

---

### Post by Quackers on 2011-10-08
It should be fine :-)

---

### Post by ClientAlive on 2011-10-08
> **Quackers said:**
> It should be fine :-)


Right on. Thanks. I have clonezilla running now to back up that partition . . . Then I'm off!


:)

Wish me luck!

---

### Post by Quackers on 2011-10-08
Good idea :-)
Good luck!

---

