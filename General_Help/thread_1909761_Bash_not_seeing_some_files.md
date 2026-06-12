---
title: "Bash not seeing some files"
date: 2012-01-15
forum: General Help
---

### Post by Wise Ferret on 2012-01-15
I had a ppa mess, had to remove many packages, but finally purged the offending repositories and re-installed ubuntu-desktop successfully. All packages on my system are now from official repos. 3d, sound, gnome-shell, firefox, libreoffice - all works well.

However, there is a weird problem. Some programs would not run, because the system refuses to recognise their existence. For example, trying to run wine:
```
yotam@aku:/usr/bin$ ls -l ./wine
-rwxr-xr-x 1 root root 9684 2011-09-20 01:39 ./wine
yotam@aku:/usr/bin$ ./wine
bash: ./wine: No such file or directory

```
This happens with other programs too, some of them in my user directory (atom zombie snasher - great game!). What is going on? Is my system crazy now? How can I make it recgnise its own files again?

---

### Post by Wise Ferret on 2012-01-15
Solved!
I found this:
[http://www.linuxquestions.org/questions/linux-software-2/bash-no-such-file-or-directory-when-file-actually-exists-860893/](http://www.linuxquestions.org/questions/linux-software-2/bash-no-such-file-or-directory-when-file-actually-exists-860893/)
This was a 64-bit issue with 32-bit programs. I installed ia32-libs-multiarch:386, and now everything works again.

---

