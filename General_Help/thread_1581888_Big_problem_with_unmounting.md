---
title: "Big problem with unmounting"
date: 2010-09-25
forum: General Help
---

### Post by FrolicsomeGaiety on 2010-09-25
So, the CD drive on my laptop doesn't work. I'm trying to install a 5 disk (iso) game (Baldur's Gate II). I've tried Gmount iso and the command line to mount CD1's iso (successfully), Wine prompts the install.exe just fine, but when then the install wizard prompts me for CD2 it is impossible for me to unmount it- in either Gmount or command line. When I click "unmount" in Gmount it simply ignores my click... CD1's info stays stubbornly in my virtual drive (media/cd) until I exit the install wizard- then, it mounts and unmounts fine. But that doesn't exactly help me install the game.

Attempting to unmount via right-click gives the error message "umount: /media/cd is not in the fstab (and you are not root)".  "sudo mount -t iso9660 -o loop /home/frolicsomegaiety/ISO/BG2_CD1.iso /media/cd" is the command that successfully mounted, but again, "umount media/cd" gives the same error in the terminal as the error message above: /media/cd is not in the fstab.

Please help... been digging around for hours.

---

### Post by lisati on 2010-09-25
Duplicate of [http://ubuntuforums.org/showthread.php?t=1581911](http://ubuntuforums.org/showthread.php?t=1581911)

---

