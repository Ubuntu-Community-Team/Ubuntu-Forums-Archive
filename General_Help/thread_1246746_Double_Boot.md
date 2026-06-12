---
title: "Double Boot?"
date: 2009-08-22
forum: General Help
---

### Post by ripper9100 on 2009-08-22
Hi,

At the moment I'm double booting with XP and Jaunty. I have the Professional Edition of Windows 7 and I would like to replace XP with 7. My question is would doing this cause issues with Ubuntu since I've heard that it's better to install Windows before installing Ubuntu?

---

### Post by Nburnes on 2009-08-22
Heres a good answer

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by ripper9100 on 2009-08-22
Thanks for the prompt reply.

---

### Post by swerdna on 2009-08-22
If you want to replace xp you might use the "files & settings" transfer wizard to take your data off.

Install windows7 onto the xp partition, formatting it in the first part of the install. That will overwrite the Grub code in the Master Boot record. So then reinstall Grub to the MBR with it's pointer leading to the Ubuntu root partition (and thus to Grub's menu.lst which already has an entry for windows).

When the dust settles, use the files and settings transfer wizard to restore your data into the new windows.

PS I also read somewhere that if you purchased the right copy of windows 7 you can avoid all of the above by simply upgrading xp to win7.

---

