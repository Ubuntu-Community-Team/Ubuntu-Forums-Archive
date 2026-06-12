---
title: "Grub WinXP invalid signature"
date: 2011-03-13
forum: General Help
---

### Post by jvanc on 2011-03-13
I'm having problems with Grub booting my WinXP drive.  I'm running Ubuntu 10.10 on a master IDE drive, and WinXP Pro on slave IDE drive.  Grub reports 2 errors: "no such device: 56ec96a1ec967ac7" and "invlaid signature". I've already tried "sudo update-grub" with no luck.  I've tried to edit the Grub menu option for WinXP, but I'm not sure what I should edit it to. The problem is not with the WinXP drive because it boots fine if I make it the master drive. Attached is my results.txt from [boot info script]("http://ubuntuforums.org/showthread.php?p=10554586").

---

### Post by YesWeCan on 2011-03-13
Are you able to boot XP directly from bios (not using Grub)?

---

### Post by jvanc on 2011-03-13
Yes.  You just answered my question with your question.  I overlooked the obvious.  I didn't get the BIOS setup correctly.  I was so focused on GRUB that I didn't event think to update the BIOS when I added the second HD.  I feel dumb.  Thanks for the reply.

---

