---
title: "cannot go to windows thru grub"
date: 2010-06-17
forum: General Help
---

### Post by rrsch on 2010-06-17
i have windows xp on one disk, and installed ubuntu 9.1 on another disk. grub worked fine (it was an older version). i downloaded 10 must not have selected the right item, because i restarted as directed and ubuntu went to a shell. i tried several things but to no avail. i then reloaded 9.1 from my dvd and during installation it asked if i wanted to load 9.1 only(erase 10) on the disk. so i did that. it gave me some options for grub  and obviously i selected the wrong one. grub comes up and will go to ubuntu and that works fine. if i select windows xp i get a blank screen with a blinking curser in the upper left for al long as i wait. the windows option on grub indicates the disk that it is on but nothing happens.
rrsch

---

### Post by tylerwagler on 2010-06-17
I would make sure your grub installation is fully up to date via the update manager and run 

$ sudo update-grub

this will redetect the windows partition and hopefully fix the booting issue.

---

### Post by rrsch on 2010-06-28
after running sudo update-grub it listed the menu items up to the windows item then printed this: ls: cannot access /media/my: no such file or directory
found microsoft windows xp professional on /dev/sdb1

---

### Post by Mark Phelps on 2010-06-29
Looks like you may have your windows partition mounted under /media.

Unmount that and rerun "sudo update-grub".  That should generate a correct grub config file.

---

