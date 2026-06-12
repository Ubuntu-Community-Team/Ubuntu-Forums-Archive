---
title: "Error 15 At startup"
date: 2009-10-22
forum: General Help
---

### Post by CodeTBone on 2009-10-22
Hey guys, having a problem booting my computer in Jaunty, or any OS for that matter.
 
Let me start from the beginning.
 
I did a dual boot on my computer that had XP with Ubuntu, went great everything worked fine.  I started getting an error in update manager so I opened up the package manager to see what was wrong like it told me, but unfortunately my ride to school arrived and I just locked the screen and left for school at 6am.  I came home looking forward to fix this problem only to find that my brother had tried to boot windows by holding the power button down and now when I boot either OS I get one of these:
 
Ubuntu:
Error 15: File Not Found
Press any key to continue...
(Reverts to OS select menu)
 
Windows XP 
BSOD- Unmountable drive, Windows has been shut down to prevent damage to your computer.
 
So Im not really sure what exactly happened but I would greatly appreciate any insight to how this happened, and how to fix it.

Im fairly new to Ubuntu so a noob friendly explanation would be greatly appreciated.
 
Thanks Guys

Edit: Im able to boot up in the "Try Ubuntu without installing" mode off the live disc, what should I do now to find the problem?
Edit2: Booted at LiveCD and reinstalled grub according to [https://help.ubuntu.com/community/WindowsDualBoot#recovering-grub](https://help.ubuntu.com/community/WindowsDualBoot#recovering-grub)
Edit3: NTLDR Is Missing Error.

---

### Post by CodeTBone on 2009-10-23
Bump.

---

### Post by CodeTBone on 2009-10-23
Bump

---

### Post by gareththegeek on 2009-10-23
Have you tried booting linux from a live cd?

Might let you examine the disk using gparted and checkout grub settings so you have a better idea of what the problem is.

---

### Post by P4man on 2009-10-23
looks like (at the very least) grub is messed up. Could be more to it than that as well.

Anyway as posted above, boot a livecd. If the hard drive is mountable, then try reinstalling grub (google on it). With a lot of luck that would solve both ubuntu and xp problems, but i wouldnt bet on it.

---

### Post by CodeTBone on 2009-10-23
Im able to boot up in the "Try Ubuntu without installing" mode off the live disc, what should I do now to find the problem?

---

### Post by CodeTBone on 2009-10-26
Edit: Updated post.

---

