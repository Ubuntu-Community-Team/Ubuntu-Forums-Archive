---
title: "UBUNTU BootMGR message"
date: 2010-08-21
forum: General Help
---

### Post by Cenix on 2010-08-21
Using Ubuntu only, without a CD...

Is there a way I can fix my Windows BOOTMGR using Ubuntu please? Can I use the Terminal?

---

### Post by philinux on 2010-08-21
> **Cenix said:**
> Using Ubuntu only, without a CD...

Is there a way I can fix my Windows BOOTMGR using Ubuntu please? Can I use the Terminal?

See section 16. [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by dino99 on 2010-08-21
windoz cd fix windoz issue, ubuntu cd fix ubuntu issue

---

### Post by oldfred on 2010-08-21
Actually with XP you use Linux, either Ubuntu or any of the system rescue type CDs to repair almost everything. But with Vista or 7, Dino99 is correct that many errors need windows tools to fix.

BootMgr missing or compressed/edit BCD
[http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391)

---

### Post by Cenix on 2010-08-21
Thanks [[COLOR=#D40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083").

dino... You fail. lol... Like really.

---

### Post by Lateralus138 on 2012-05-07
I know that this is an old thread, but I recently fixed my Bootmgr via Ubuntu and I thought I might add how I did it as it pertains to this thread. I am so/so new with Linux, but I have used it enough to know that it is great for fixing and editing Windows files.

This is for anyone who doesn't have their Windows install disc or for those (like me) that have a custom Windows install and can not repair from the disk.

This is very simple:

1. Boot into Ubuntu (or the Ubuntu live from disk).

2. Locate your Windows partition and open whatever your Windows root drive is (C:\, D:\ etc...).

3. Inside of your root drive you will see (or should see) a couple of bootmgr files that could say bootmgr, bootmgr~1, bootmgr~2 etc. Bootmgr, of course, is the corrupted file so compress that file just in case (in case I don't know what, I back up everyting) and delete it and then rename one of the other bootmgr~2 files to bootmgr. I am not sure which would be the last backup file, but if you only have 2 files then it doesn't matter.

4. Reboot. If that bootmgr is corrupt as well then repeat these steps for another file.

I had 6 bootmgr, 5 of which were backups and 5 of all 6 were corrupt. I was lucky to have one.

---

### Post by oldos2er on 2012-05-07
Closed. Please don't bump old threads.

---

