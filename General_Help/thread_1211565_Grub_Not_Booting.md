---
title: "Grub Not Booting"
date: 2009-07-12
forum: General Help
---

### Post by lakelovers on 2009-07-12
I'm running 9.04, but currently running on a live 8.04 CD. Grub stopped working. I followed instruction on this forum for fixing Grub but so far nothing has worked. 

find /boot/grub/stage1
root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

I did this twice. Neither time resulted in booting my computer so something is really screwy.

I also tried using the Super Grub CD, and still couldn't boot my Ubuntu.

How can I solve this problem?

---

### Post by lindsay7 on 2009-07-12
try this

Originally Posted by lindsay7 View Post
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
__________________

---

### Post by lakelovers on 2009-07-12
Okay, I've done this two times without success, but I'll do it again and let you know. I also went into the recovery mode and got the message: "dev sda1 file system in error" or words to the effect. Then continued with many fixes in the recovery mode and received a final message: "Could not start the X server due to some internal error."

---

### Post by lakelovers on 2009-07-12
Well I'll be darned. Third time's a charm. It worked. Thanks, Lindsy7. Now, to add another pain in the axx, the cursor (mouse) stopped working a week or so ago, and the only way I can get it working is to do a hard start. And it could be the the hard starting is what currupted Grub. I've searched for answers on the cursor problem by have not found a solution, though I've read the inference that it may be a 9.04 problem. Any ideas?

---

### Post by blueridgedog on 2009-07-12
Based on your first post, you were leaving out the root command.

---

### Post by lindsay7 on 2009-07-12
Have you looked at System/preferences/mouse and tried changes some of the settings?

---

