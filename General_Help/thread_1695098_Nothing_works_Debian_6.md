---
title: "Nothing works? Debian 6"
date: 2011-02-25
forum: General Help
---

### Post by toxic9813 on 2011-02-25
I just installed Debian "squeeze" and after getting everything installed, I can't use the terminal for anything, and any .deb I install does not have a shortcut, so I need to go to File System and search for my program to get it to start.

Any help on this?
I get this message in the terminal. (For example I am trying to install java the way the Debian wiki says, apt-get install sun-java6-jre)

As sudo apt-get:```
 toxic is not in the sudoers file.  This incident will be reported.
```

as apt-get: ```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

and if I type " su -" and then type my password, and try apt-get again,```
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

What is going on?

---

### Post by dino99 on 2011-02-25
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

[http://ubuntuforums.org/showthread.php?t=1251796](http://ubuntuforums.org/showthread.php?t=1251796)

[http://www.debian.org/releases/stable/installmanual.en.html](http://www.debian.org/releases/stable/installmanual.en.html)

---

### Post by khelben1979 on 2011-02-25
Make sure that no Package Manager is running, because it locks up and don't allow apt-get to install anything.

Login as root or open up the Package Manager with super user priviliges to solve this issue. You cannot install system packages as a regular user.

---

### Post by cbennett a7xftw on 2011-02-25
try reinstalling it, not the os but the debian 6  it could of screwed somthing up

---

