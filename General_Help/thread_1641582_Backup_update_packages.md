---
title: "Backup update packages"
date: 2010-12-09
forum: General Help
---

### Post by twitty1437 on 2010-12-09
Hi everyone, some questions:
1. when we install package and run update manager, are all the packages stored in /var/cache/apt/archives ?
2. let's say i make a copy of all the packages i installed and from update, store them in a backup drive. How do i make a freshly installed Ubuntu to copy/use these packages instead of downloading them from the internet?

thanks :)

---

### Post by plucky on 2010-12-09
> 1. when we install package and run update manager, are all the packages stored in /var/cache/apt/archives ?

Yes

> 2. let's say i make a copy of all the packages i installed and from update, store them in a backup drive. How do i make a freshly installed Ubuntu to copy/use these packages instead of downloading them from the internet?

If the correct package is in /var/cache/apt/archives it will be used before it is downloaded from the internet.It will only download if an updated package is in the repository.

I sometimes use a package called APTonCD for transferring packages between machines using just the .iso file created by APTonCD copied to a pen drive.Saves using CDs.  


Good Luck

---

### Post by twitty1437 on 2010-12-09
thanks a lot for the very useful tips!

---

