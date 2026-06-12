---
title: "[Cli] List all the available packages in a repository"
date: 2010-09-18
forum: General Help
---

### Post by edonan on 2010-09-18
Hello,
I can't manage this simple task: I want to get a list of the packages that are inside a specific repository which is in my sources list from command line.
Basically this is what Synaptic does when you filter with "Source".
How can I do that?
Thanks!

---

### Post by mc4man on 2010-09-18
All of the package lists are in  /var/lib/apt/lists, so see what info you want in a list.

for instance, just basically a simple a-z listing of all the names in main here (may pull some add. info for some, i'm sure the below can be improved

```
grep Package /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick_main_binary-i386_Packages > packages-main.txt 2>&1

```

---

