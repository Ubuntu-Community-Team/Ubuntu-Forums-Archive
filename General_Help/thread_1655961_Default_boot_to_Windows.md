---
title: "Default boot to Windows?"
date: 2010-12-30
forum: General Help
---

### Post by clangford84 on 2010-12-30
Gents,
How do I switch in the boot screen for it to boot to Windows if I do not specify otherwise in the 10 seconds it allows?  Is it possible to extend this 10 seconds?  Also, I have about 10 Ubuntu options on the boot screen I assume from all the updates.  How do I delete a couple of these options?  Anybody's help would be much appreciated.  Thanks

Oh, I am running Ubunti 10.4 with a partitioned drive with Windows 7.

---

### Post by Quackers on 2010-12-30
Welcome to UF.
You can make Windows the default OS by installing Startup Manager which is available via synaptic package manager. You can then change the default OS.
However, this will need re-doing after every grub update.
If you want to make the change permanent you can edit /etc/default/grub using the guide below. This guide also explains how to change the default timeout from 10 seconds.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by clangford84 on 2010-12-30
Alright, that was a quick response.  Seemed to have solved most of it.  But, I still have all these ubuntu boot options that I would like to slim down.  It would be nice to have a selection option for Ubuntu, and then one for Windows.  Not 10 for Ubuntu, and one for windows which I have to scroll all the way to the bottom for.  Any way to change this?

---

### Post by Quackers on 2010-12-30
What isn't in that first link is in this one :-) everything you need.

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by clangford84 on 2010-12-30
Thanks again Quackers.  Your help is much appreciated.

---

### Post by Quackers on 2010-12-30
You're welcome :-)
It looks a bit daunting but it's ok if you take a bit of care.

---

