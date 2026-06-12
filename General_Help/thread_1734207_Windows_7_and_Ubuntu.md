---
title: "Windows 7 and Ubuntu"
date: 2011-04-20
forum: General Help
---

### Post by OpenGLSecond on 2011-04-20
So, because of recen happenings, I decided to remove Ubuntu and give all its space to Windows 7. So, I've got one disk(320 GB HDD). There are two partitions. One is C drive, there is windows xp. And the other is D drive, it half windows 7 half ubuntu. So, I'm total noob, and need help. What program to use, how,.... I just need a little "instructions"
 
Thnx in advance

---

### Post by earthpigg on 2011-04-20
hi,

having skimmed both of these guides, i believe either will do just fine.

[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)

---

### Post by ghostborg on 2011-04-20
Funny, I had the opposite happenings. hehe.
Good Luck to you.

---

### Post by ashickur.noor on 2011-04-20
> **OpenGLSecond said:**
> So, because of recen happenings, I decided to remove Ubuntu and give all its space to Windows 7. So, I've got one disk(320 GB HDD). There are two partitions. One is C drive, there is windows xp. And the other is D drive, it half windows 7 half ubuntu. So, I'm total noob, and need help. What program to use, how,.... I just need a little "instructions"
 
Thnx in advance
I don't undestand your problem at all.

---

### Post by Raan03 on 2011-04-20
> **OpenGLSecond said:**
> So, because of recen happenings, I decided to remove Ubuntu and give all its space to Windows 7. So, I've got one disk(320 GB HDD). There are two partitions. One is C drive, there is windows xp. And the other is D drive, it half windows 7 half ubuntu. So, I'm total noob, and need help. What program to use, how,.... I just need a little "instructions"
 
Thnx in advance
So if I understand correctly: you went back to Windows 7 and deleted your Ubuntu (how did you install and remove Ubuntu?)

You have two partitions, 1 with XP and one with 7 (& past Ubuntu on it). It depends on how you installed Ubuntu (Wubi? Install on boot?) before we can help you out.

---

### Post by OpenGLSecond on 2011-04-20
> **Raan03 said:**
> So if I understand correctly: you went back to Windows 7 and deleted your Ubuntu (how did you install and remove Ubuntu?)
 
You have two partitions, 1 with XP and one with 7 (& past Ubuntu on it). It depends on how you installed Ubuntu (Wubi? Install on boot?) before we can help you out.
 
You didn't understand me. One partition is Windows XP(150 GB). Other partition(170 GB) is sahred. Windows 7 and Ubuntu sharer it. 7 80GB and Ubuntu 90 GB. What i want to do, is uninstall it and give its 90 GB to windows 7. Was I clearer now?

---

### Post by Mark Phelps on 2011-04-20
> **OpenGLSecond said:**
> You didn't understand me. One partition is Windows XP(150 GB). Other partition(170 GB) is sahred. Windows 7 and Ubuntu sharer it. 7 80GB and Ubuntu 90 GB. What i want to do, is uninstall it and give its 90 GB to windows 7. Was I clearer now?

You were actually clear the first time ...

Ubuntu installed via Wubi is the same as installing a Windows app.  You remove it the same way you remove a Windows app --> Control Panel --> Programs and Features.

If after that, in Win7, you still see an entry in the OS selection menu, recommend you install EasyBCD from NeoSmart Technologies.  That provides an app allowing you to easily modify the Win7 boot loader options.  You can then use that to remove the old Ubuntu entry.

---

### Post by drewesq on 2011-04-20
if you want to be just using windows xp then just go into disk management and format your D:
 
If you want to use dual boot  7 & XP then Ubuntu (if not WUBI) must have had its own partition so format that.
 
Do any formatting to NTFS.

---

### Post by Mark Phelps on 2011-04-20
> **drewesq said:**
> if you want to be just using windows xp then just go into disk management and format your D:

The OP said > and give all its space to Windows 7, so they want to use Win7.
 
> If you want to use dual boot  7 & XP then Ubuntu (if not WUBI) must have had its own partition so format that.

The OP said > I decided to remove Ubuntu.  They don't want a dual-boot; they want Ubuntu gone.
 
>  Do any formatting to NTFS.
No formatting is needed.  This reads like a Wubi installation and all the OP has to do is remove Ubuntu to reclaim all the space it took.

---

