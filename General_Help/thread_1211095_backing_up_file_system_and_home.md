---
title: "backing up file system and home"
date: 2009-07-12
forum: General Help
---

### Post by graphicsxp on 2009-07-12
Hi,

I've installed ubuntu a couple of months ago and since then I've installed many more packages and I've also changed some settings in various places including xorg.conf. I've also installed virtualbox and I have windows xp running as the guest os, with many software installed.

Now I fear a crash from which I could not recover and I would have to re-install and reconfigure everything, which would take days....

How can I backup my entire system (including configurations settings) so that if worse come to worse, I will just have to reinstall ubuntu and run a restore. Please give me some hints on how this can be done. 

Thanks

---

### Post by jskandhari on 2009-07-12
Simple

goto
Places>Computer

click on File System
after that hit "crtl+h" or goto tool and tick the show hidden files button after that sellect all and copy it to a HDD for backup...

after fresh install simply goto File System again and paste all the prior folders and Ubuntu Gr8 will pick up the changes automatically at max log out  and log in again.

Alternate

Open Archive Manager
new
and select the whole file system ( but remember the hidden files should be ticked for display)
and create a archive in .7z/.tar.gz format and then can extract the min file system directly and merge all.

NOTE::Provided you are doing on same version elsewise don't copy the system version folders and boot folder.
## Perform all the operation as root use "sudo" command.

---

### Post by sasho_zl on 2009-07-12
Check this out: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

