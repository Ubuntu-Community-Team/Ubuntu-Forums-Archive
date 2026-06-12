---
title: "Using Symantec Ghost 11 (ghost32.exe) with Wine"
date: 2009-09-21
forum: General Help
---

### Post by maxpoweron on 2009-09-21
At my job I need to be able to "Ghost" PCs.  Our current process is BARTPE bootable CD.  It works very well, but takes forever to boot due to all the drives it requires to load onto a PC.

What I would like to do is boot from my bootable 16GB USB flash drive with Ubuntu 9.04 installed.  

I installed Wine and copied over ghost32.exe.  I can get ghost32 to run under Wine, but I cannot get ghost to see the local HDD (IDE or SATA).

Is there a way to have ghost32 reconize the local HDD (IDE and SATA so I can load or restore an image?

---

### Post by khelben1979 on 2009-09-21
I would say to not expect too much from Wine. If Symantec Ghost is supported officially you can always give the Wine developers a bug report describing the problem.

Other than that, I would advice you to find some Linux native application which does the same thing (don't know if it exists).

---

### Post by mike555 on 2009-09-21
why not try " CloneZilla " it's free and works very well ...

---

### Post by maxpoweron on 2009-09-21
I was going to look into clonezilla when my schedule permits.  Will clonezilla work with gho and ghs files created using Symantec Ghost?

---

