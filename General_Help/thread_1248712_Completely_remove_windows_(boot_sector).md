---
title: "Completely remove windows (boot sector)"
date: 2009-08-24
forum: General Help
---

### Post by Luppi on 2009-08-24
Hi All,

I have reached a stage where there is no more need for my Windows partition (still have a few things to run on Windows but that is solved thanks to VirtualBox).

Now I want to delete my windows partition an use it's space for linux.  However gparted does not allow me to play with the windows ntfs partition and, besides that, my boot sector (where grub lies) appears to be in the windows partition as well.

Is there a way to do it and can anyone point how to do it?

Thanks
Luppi

---

### Post by zkriesse on 2009-08-24
Use the live cd to change the partition.

---

### Post by Luppi on 2009-08-24
Thanks Zachk could you provide further details?  I can boot from the live cd, execute gparted and destroy the partition... what happens with the boot sector?  will it still be there?  do I have to resize the linux partition before booting again from my hd?   Any precautions (besides backup)?

---

### Post by zkriesse on 2009-08-24
I would definitely back up to an external if you know how to re-load back on the internal. But getting rid of the windows partition to make it just Ubuntu requires a full re-install. I think so go to the links in my signature just to make sure. AND GOOGLE IT! WAIT!!!!!!!!!!!!!!!!! Found this thread on here....check it out FIRST! [http://ubuntuforums.org/showthread.php?t=502450](http://ubuntuforums.org/showthread.php?t=502450)

---

