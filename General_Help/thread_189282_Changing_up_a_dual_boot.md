---
title: "Changing up a dual boot"
date: 2006-06-05
forum: General Help
---

### Post by Cable on 2006-06-05
Currently, I have a dual boot set up between Win XP Pro and Win XP Pro x64.  I never ever use x64 (crappy driver support, etc.), and am going to replace that with Ubuntu.  Before I install Ubuntu, I want to get my computer to only boot into Win XP Pro, and wipe XP x64 from my hard drive.  How do I get rid of XP x64?

---

### Post by hw-tph on 2006-06-05
I guess this is a Windows question really, but since it's for a good cause I'll bite. :)

If I recall correctly there is an entry for administrating the boot loader in System properties, or you can just edit your C:\boot.ini (requires Administrator privileges, obviously) and remove the entry you don't want.


Håkan

---

### Post by Loffe_ on 2006-06-05
You do have Win64 on a separate partition, right?

Then just remove that partition and install Ubuntu to the new empty space.

Remember to make a backup of all important data!!
It is sad when people without backups blame their data loss on linux](*,)

---

