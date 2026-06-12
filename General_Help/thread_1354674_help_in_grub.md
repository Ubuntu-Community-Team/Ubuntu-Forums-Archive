---
title: "help in grub"
date: 2009-12-14
forum: General Help
---

### Post by varungosain113 on 2009-12-14
i have dual boot with xp and ubuntu i want that while showing grub at starting ( choose b/w windows and linux) it doesnt show windows and boot automatically with linux??i.e. i want to hide windows partition

and also how to unhide it

---

### Post by raymondh on 2009-12-14
> **varungosain113 said:**
> i have dual boot with xp and ubuntu i want that while showing grub at starting ( choose b/w windows and linux) it doesnt show windows and boot automatically with linux??i.e. i want to hide windows partition

and also how to unhide it

which version GRUB are you using?  Better yet, which version Ubuntu are you using?  Also, did you install Ubuntu in it's own partition or did you install ubuntu "inside windows" (referred to as WUBI)

depending on your answer, you will have to do some editing.

For GRUB legacy

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

For GRUB2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If you are using 9.04 or earlier, and prefer not to manually edit GRUB, you can open synaptic and search for/install startupmanager.  It is GUI-based and also writed to the menu.lst.  For your preferences, select Ubuntu as the default.  For the 'direct-to-ubuntu-startup', just select the appropriate time.  For instant access, you may select 0.  I prefer 1 because it still gives me a split-second to press the space key if I changed my mind.

---

