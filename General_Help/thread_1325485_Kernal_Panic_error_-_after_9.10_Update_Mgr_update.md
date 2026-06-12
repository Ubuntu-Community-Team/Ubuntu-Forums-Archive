---
title: "Kernal Panic error - after 9.10 Update Mgr update"
date: 2009-11-13
forum: General Help
---

### Post by SYBU on 2009-11-13
**Kernal Panic error - after 9.10 Update Mgr update** 
Newbie to Ubuntu/Linux. I recently upgraded from 9.04, which was working fine on dual boot PC Compaq Presario - XP, to 9.10. Last night Update Mgr performed some security updates. This morning I restarted the 9.10 and it froze during the boot process. Here are the boot screen results:

[ Linux-bzImage, setup=0x3400, size=0x3b26e0]
[ Initrd, addr=0x37864000, size=0x78b4f5]
[ 0.963213] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2) 
"FROZE"


I also tried the recovery mode boot option and it freezes as well. I can boot into XP fine.

Again, I'm new to Linux and would welcome some help with my next steps to resolve this issue. thanks.
SYBU

---

### Post by Fire_Chief on 2009-11-13
By chance, when you did the updates, did you have a dialog box come up asking about which grub-pc configuration to use? Not sure what other causes may be here but it's a reasonable guess that grub got goofed.

---

### Post by jotto! on 2009-11-13
I have the same problem, same error.
Some one said to check my menu.lst file but I dont seem to have one...could this be the problem?

---

### Post by Fire_Chief on 2009-11-13
No, 9.10 uses Grub2 which does not use the menu.lst file anymore.
See more on Grub2 here [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by jotto! on 2009-11-13
Dont want to hijack the thread but I only have a grubenv file in the grub folder...no grub.cfg?????

Fire_Chief, you have a PM! ;)

---

### Post by jgwhite5 on 2010-04-08
I had a very similar issue to this, directly after an update was applied. I was getting the following error:

[FONT=Fixedsys][1.006051] Kernel panic - not syncing : VFS : Unable to mount root fs on unknown - block (8,1)[/FONT]

This is what I did, and it worked perfeclty for me:

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90)

Hope it helps you as well!

---

