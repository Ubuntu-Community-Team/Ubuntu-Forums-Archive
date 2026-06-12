---
title: "2 quick questions"
date: 2006-04-12
forum: General Help
---

### Post by thunderfox933 on 2006-04-12
1. installed ubuntu 5.10 with windows xp home. When i wanted to boot into windows windows wasnt there what did i do wrong.

2.is 3gb enough for ubuntu

---

### Post by Ubuntuud on 2006-04-12
3GB is enough to install, but not for much software nor documents.

---

### Post by intangir1999 on 2006-04-12
Thunder, see this thread [http://www.ubuntuforums.org/showthread.php?t=159098](http://www.ubuntuforums.org/showthread.php?t=159098)
and 3G is enough to install, however, you may want at least another 3G for apps and file storage.  Nowadays, a good 20G is *recommended* for everyday system use.

---

### Post by Sef on 2006-04-12
> 1. installed ubuntu 5.10 with windows xp home. When i wanted to boot into windows windows wasnt there what did i do wrong.

Did you do a manual install or an automatic install?  If you did the latter, then it overwrote windows.   If the former, then maybe GRUB did not detect windows for some reason.

Do this from the terminal (Applications > Accessories > Terminal):  fdisk -l, then copy and paste here what it says.

---

### Post by Ramses de Norre on 2006-04-12
Think you'll need to do sudo fdisk -l and type in your user password.
3GB isn't much, imagine you would run windows on a 3GB drive.. You wont have many space for programs, multimedia files, documents etc.

---

