---
title: "Resoring GRUB...Help!"
date: 2009-11-21
forum: General Help
---

### Post by Himself2007 on 2009-11-21
Hello

I had Ubuntu 9.10 karmic Koala that was running nice.
I also have XP-Pro on separate HD.
I just restored a previous Windows XP backup.
But now I think XP erased my GRUB because Ubuntu does not load anymore.
No GRUB appearing! But before it did!
I read that this happens when you restore XP.
I made a google search and found this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Murphy's law!
 It says that "it does not work for Ubuntu Karmic Koala ..."

I did another search..."unetbootin-windows-377.exe" and does not seems to work.

Anybody has a solution for this?
Help!

Luc

---

### Post by sisco311 on 2009-11-21
Try this:
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")

---

### Post by HappyFeet on 2009-11-21
Next time, unplug your ubuntu drive before reinstalling xp.

---

### Post by Himself2007 on 2009-11-21
> **sisco311 said:**
> Try this:
[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2")

I tried what you suggested.
But none of the solutions worked.
These solutions by the way did not take into account that there was another OS on the computer.
Anyway!
I just erased the Ubuntu H-disk and am prepared to reinstall karmic on it.
With this, new GRUB will be created aside Windows XP.
And I will just restore a backup I did this morning before doing all modifications.
A restore without the previous MBR, naturally.
Anyway, as I understand, seroius changes have been made on the Windows's MBR, not on Ubuntu's. 
Thanks anyway!

Luc

---

### Post by Zoot7 on 2009-11-21
> **HappyFeet said:**
> Next time, unplug your ubuntu drive before reinstalling xp.
+1

I always do this with all my hard drives. it's always best only to have Windows able to only able to access the hard drive it's going to go on, on account of it's habit of taking over the whole PC.

---

