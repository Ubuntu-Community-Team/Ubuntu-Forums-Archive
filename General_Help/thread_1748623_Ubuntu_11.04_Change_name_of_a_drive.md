---
title: "Ubuntu 11.04: Change name of a drive?"
date: 2011-05-03
forum: General Help
---

### Post by metrogdor22 on 2011-05-03
I'm trying to change the permissions of a folder within an external drive called "New Volume"(that's the name of the drive). When in the terminal, changing directories is impossible. I've tried
$cd "New Volume", and 
$cd New\ Volume

But neither work. It just says it can't find the directory. How can I change the name of the drive to not have a space in it?

---

### Post by andrewthomas on 2011-05-03
You can relabel the drive with disk utility, yet it is probably mounted under media. 
 
So if you 
 
```
 
cd /media/New<TAB>

``` auto-complete will add the backslash and space for you.

---

### Post by dcstar on 2011-05-04
> **metrogdor22 said:**
> 
.........
How can I change the name of the drive to not have a space in it?

Use **gparted** or the **Disk Utility.**

---

