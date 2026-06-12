---
title: "printer driver f***ed everything up"
date: 2006-06-21
forum: General Help
---

### Post by tlo on 2006-06-21
i tried installing a driver for my printer. there were drivers on the printer's website, but they were tested for like debian 3.01 or something. anyway, i tried downloading the packages and installing them like they said, but they didnt quite work. anyway, now im trying to install other packages (nvidia-glx) and it says that package mfc6800lpr needs to be reinstalled, but there is no valid package, and quits. how do i fix it and set apt back to normal?

---

### Post by uteck on 2006-06-22
From this [post]("http://www.ubuntuforums.org/archive/index.php/t-105056.html") it says that removing the file /var/lib/dpkg/info/mfc6800lpr.postrm should fix the problem.

---

### Post by tlo on 2006-06-25
[QUOTE=uteck]From this [post]("http://www.ubuntuforums.org/archive/index.php/t-105056.html") it says that removing the file /var/lib/dpkg/info/mfc6800lpr.postrm should fix the problem.[/QUOTE]

i deleted that file and it still didnt work. then i deleted all of the mfc6800lpr files, and it still doesnt work.

---

### Post by taurus on 2006-06-25
Did you remember to
```

sudo apt-get update

```

---

### Post by tlo on 2006-06-25
yes, and i still cant apt-get anything. apt-get update is the only thing that works.

a little more detail on what screwed everything up: i tried to install the lpr driver from brother's website, using their instructions.```
dpkg -i --force-all xxxx.deb* (for Debian Users)
``` when i still couldnt print (come to think of it im not sure that the driver installed correctly) i tried installing the cups wrapper on top of it because the brother website told me to. i have never done a printer install, and dont know what these things are or exactly what i am doing.

---

### Post by taurus on 2006-06-25
[QUOTE=tlo]```
dpkg -i --force-all xxxx.deb* (for Debian Users)
``` [/QUOTE]
That is the strangest looking command!  Normall, you want to install everything in the directory with
```

dpkg -i --force-all *.deb

```
Are you sure that is what it (README/INSTALL/doc) told you to do???

---

### Post by tlo on 2006-06-25
im sorry, i directly copied and pasted that from the website xxxx was the package name that i installed, and the for debian bit in the parentheses was to differentiate it from the line above that was for rpm users. the command i used was
```
dpkg -i --force-all mfc6800lpr-1.1.2-1.i386.deb
```

---

### Post by tlo on 2006-06-25
bump? any help with unfubaring dpkg?

---

