---
title: "Grub Managing Software?"
date: 2011-10-18
forum: General Help
---

### Post by khoraski on 2011-10-18
This isn't really anything urgent, but my Grub tends to cause some problems and I am afraid if I try to manage it manually, I may end up making it worse. Another problem is that I have an operating system installed on a partition, but I can't access it because there is nothing in the Grub pointing to it. 

So, if any of you happen to know of a software that will easily help me manage my Grub, that would be helpful.

---

### Post by oldfred on 2011-10-19
This is not managing grub but booting:

[Boot-Repair] Graphical tool to repair the PC boot in 1 clic !
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

But you need to know what is installed where an what drive/system you are booting. Boot repair has the boot)info script that outputs tons of detail which may be too much for a new user but does tell what is where.

---

### Post by seawolf167 on 2011-10-19
What are the specific problems you are having? To recognize the other operating system usually

```
sudo update-grub
```

will do the trick. Does this not work for you?

---

### Post by plucky on 2011-10-19
> **khoraski said:**
> This isn't really anything urgent, but my Grub tends to cause some problems and I am afraid if I try to manage it manually, I may end up making it worse. Another problem is that I have an operating system installed on a partition, but I can't access it because there is nothing in the Grub pointing to it. 

So, if any of you happen to know of a software that will easily help me manage my Grub, that would be helpful.

This [Grub Customizer](http://ubuntuforums.org/showthread.php?p=10340183#post10340183) might help.

Also [Grub Title Tweaks](http://ubuntuforums.org/showthread.php?t=1287602&highlight=drs305+grub)

Good Luck

---

