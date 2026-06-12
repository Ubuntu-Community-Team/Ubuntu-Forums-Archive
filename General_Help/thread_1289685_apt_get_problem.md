---
title: "apt get problem"
date: 2009-10-12
forum: General Help
---

### Post by elsteamola on 2009-10-12
Hello All:

I've encountered this several times lately, and it seems to be Ubuntu's biggest weakness.

Here's what I get:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/do.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Please help! 

Thanks

elsteamola

---

### Post by Teabicky on 2009-10-12
Hi,  I found this thread, hopefully there is a solution here.

[http://ubuntuforums.org/showthread.php?t=1167744](http://ubuntuforums.org/showthread.php?t=1167744)

---

### Post by sisco311 on 2009-10-12
try:
```
sudo mv /var/lib/apt/lists/ /var/lib/apt/lists-backup
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

EDIT: too late. :)

---

