---
title: "Error Reading Package Lists"
date: 2011-05-20
forum: General Help
---

### Post by ben_nuttall on 2011-05-20
Fairly new install of 11.04, installed from CD I burned from ISO.

It's been updating fine up to now but all of a sudden started giving these errors.

This is from Terminal [FONT=Courier New]sudo apt-get update[/FONT] attempt:

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```Plan of action?

---

### Post by spikoley on 2011-05-20
It looks like [this thread]("http://ubuntuforums.org/showthread.php?t=863742") worked for a lot of people.

> Actually, just fixed the problem using:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

All good now.

---

