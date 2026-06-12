---
title: "access denied to transmission"
date: 2011-05-29
forum: General Help
---

### Post by cbwviews on 2011-05-29
Transmission unable to access ntfs drive after installing storage device manager.  i am new to Ubuntu, and I like Natty, but I wanted to auto mount the ntfs drives, and after running SDM, the drives mount at boot, but I can't mount them manually.  In addition, Transmission is denied access to the drives where the files are located.  I am not too familiar with the command line, but can follow instructions.  If anyone can tell me the settings to use in the storage device manager assistant for users, groups etc, I will appreciate the help.

---

### Post by cbwviews on 2011-05-29
Hi, as an update, I have installed ntfs config tool, and write enabled drives, and transmission still can not access, premission denied.
Currently the only block checked in STM is mount at boot.
Thanks,,
Carl

---

### Post by cbwviews on 2011-05-30
Hi, update 2 for anyone with a similar problem.  I uninstalled SDM  and learned how to edit fstab from command line.  That solved the access problems.   However, Transmission was still denied permission.  So I uninstalled Transmission, then reinstalled it, and now works fine.  It seems the way to correct problems more accurately, is by direct editing.  Forget the mini-programs that are supposed to make it easier.

---

