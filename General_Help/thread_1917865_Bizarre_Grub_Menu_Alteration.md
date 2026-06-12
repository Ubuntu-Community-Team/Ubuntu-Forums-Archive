---
title: "Bizarre Grub Menu Alteration"
date: 2012-01-30
forum: General Help
---

### Post by SevenThunders on 2012-01-30
I recently updated a lot of packages in my Ubuntu 11.10 system, including some nvidia drivers and some Xorg code along with some changes in some core Ubuntu packages.  It seemed to go OK but oddly my Grub Menu changed so that the top two entries included the words "Linux Mint Fluxbox".

Now I had some contamination with some Linux Mint repositories earlier as described here:
[http://ubuntuforums.org/showthread.php?t=1893610](http://ubuntuforums.org/showthread.php?t=1893610)

But my sources.list is clean and contains no pointers to a mint repository.  Moreover I have never installed a fluxbox version of linux let alone a linux Mint version.

How could this have happened? Is the grub menu updated by some different mechanism?

---

### Post by drs305 on 2012-01-30
This error is the first of its kind for me, but let's see what we can find.

First, check the contents of */etc/lsb-release*:
```
cat /etc/lsb-release

```

If that doesn't contain the odd name, then check your */etc/default/grub* file to see if it has a GRUB_DISTRIBUTOR listing. If it does, and it matches the titles, place a # at the start of the line or delete the line.

If it doesn't, if you add it you may be able to 'restore' the "Ubuntu" title to your menu:
> GRUB_DISTRIBUTOR="Ubuntu"
Save the file, then update grub.

---

