---
title: "Trying to upgrade"
date: 2011-12-28
forum: General Help
---

### Post by CraigYoung on 2011-12-28
I have Ubuntu 10.04 . I want to upgrade to 10.04 but when I try it says I have insufficient space. My drive is  8GB fixed drive and all I have on it is Ubuntu and Quicken with a windows emulator (Crossover). Photos, Documents, and Quicken data are all kept in a 16Gig expansion card. 

I have tried to take off programs but it still says I have to free up 162-175 MB. 

How can I clear up some space?

Thanks

---

### Post by wolfen69 on 2011-12-28
There's usually a bunch of non-needed stuff in /var/cache/apt/archives

You can delete all the .deb files in there. (not the *partial* folder) But you need superuser permissions.

```
gksudo nautilus
```
and navigate to the folder I mentioned. You could also clear your firefox cache also.

I usually open nautilus and go to edit>preferences>behavior and add a *delete* command to right click, so I don't have to empty the trash after. But that's up to you.

---

### Post by hansdown on 2011-12-28
Welcome to the forum,CraigYoung.

"I have Ubuntu 10.04 . I want to upgrade to 10.04"....

Are you, actually trying to upgrade to 10.10?

---

