---
title: "Newbie: Folder Structure and Installations"
date: 2010-12-20
forum: General Help
---

### Post by griffen on 2010-12-20
Just installed Ubuntu on a Dell M1730 and working my way around the system. Biggest problem I'm struggling with is the folder structure and privileges. I've downloaded a few programs that don't come in DEB format. Consequently I'm not sure how they should be installed. As a windows user my assumption is that there would be a program files like folder but I'm not sure what the Ubuntu equivalent is. I've tried /opt/ but then I run into lots of privilege issues that can only be resolved by chmod. Can you advise which the location that programs should be installed in for manual installations and under which user (Standard or SU)?

---

### Post by Wtower on 2010-12-20
A lot of things to cover. First, it is important to understand that you have to leave behind your windows background and start anew. Linux and of course Ubuntu is organized in a different way. If you need to install anything I would highly recommend the Ubuntu software centre for a beginning. If you wish to learn more about the filesystem please take a read at:

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

Regards

---

### Post by QLee on 2010-12-20
[QUOTE=griffen]Just installed Ubuntu on a Dell M1730 and working my way around the system. Biggest problem I'm struggling with is the folder structure and privileges. I've downloaded a few programs that don't come in DEB format. Consequently I'm not sure how they should be installed. As a windows user my assumption is that there would be a program files like folder but I'm not sure what the Ubuntu equivalent is. I've tried /opt/ but then I run into lots of privilege issues that can only be resolved by chmod. Can you advise which the location that programs should be installed in for manual installations and under which user (Standard or SU)?[/QUOTE]

The best advice for an inexperienced new user is to install programs from the official repositories with the provided package managers. They can be trusted and the package manager makes installing easy. It isn't a good idea to just go download programs from the Internet somewhere and load them like many people do in Windows.


Here are some more links that might be helpful for a new user:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

