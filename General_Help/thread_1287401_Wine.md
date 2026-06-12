---
title: "Wine"
date: 2009-10-10
forum: General Help
---

### Post by cowboy7305 on 2009-10-10
i have just tryed to uninstall wine  via the Synoptic packages ,but it is still there in applications  ,what have i done wrong ,any help to uninstall 
many thanks

---

### Post by MelDJ on 2009-10-10
did you mark it for complete removal?

---

### Post by cowboy7305 on 2009-10-10
yes did that

---

### Post by MelDJ on 2009-10-10
post the output of sudo apt-get remove wine here and did you try restarting the computer?

---

### Post by cowboy7305 on 2009-10-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcdk5 libpt2.6.1-plugins-alsa libopal3.6.1 libkdepim4 libpt2.6.1
  libpt2.6.1-plugins-v4l2 winbind
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and i have tried restarting

---

### Post by Zoot7 on 2009-10-10
Try this:
```

rm -r ~/.local/share/applications/wine
```

That should remove the menu shortcuts. Sometimes with wine you've to do it manually.

---

### Post by shadowlemon on 2009-10-10
hmm looks weird. Can you actually start wine and run something?

---

### Post by 3rdalbum on 2009-10-10
Yes, that's correct. Wine is removed, but the programs you installed with it are still available in ~/.wine.

If the menu is bothering you, right-click on the Applications menu and choose Edit Menus, then hide the Wine menu. Then remove ~/.wine.

---

### Post by cowboy7305 on 2009-10-10
many thanks that worked

---

