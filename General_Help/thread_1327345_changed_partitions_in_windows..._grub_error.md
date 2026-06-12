---
title: "changed partitions in windows... grub error"
date: 2009-11-15
forum: General Help
---

### Post by luvgirl12345 on 2009-11-15
i changed the partitions in windows (right click computer, manage) and then restarted thinking it wouldn't cause any problems...

grub error 
unknown filesystem 
grub rescue<

I read somewhere that you had to change grub.config partition tabel...

---

### Post by oldfred on 2009-11-15
All your entries that refer to a root(x,y) and possibly your entries in /etc/fstab  (depends on whether they use UUID, label, or partition number sdxy) will have to be updated.
I would first reinstall grub:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD) 
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by oldfred on 2009-11-15
I see you dual posted. You should only post in one category as we need to see what others have already suggested to try to solve your problem.
[http://ubuntuforums.org/showthread.php?t=1327342](http://ubuntuforums.org/showthread.php?t=1327342)

---

