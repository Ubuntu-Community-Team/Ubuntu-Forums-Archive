---
title: "CLI command to Install bug fixes."
date: 2010-01-02
forum: General Help
---

### Post by OldAlgis on 2010-01-02
I installed kubuntu (9.10) from a Karmic DVD. It reports 135 bug fixes, but fails to install it from GUI.

What are the commands to install bug fixes from the CLI? (as it is the GUI that is broken).

Clearly there are bugs in a freshly installed Karmic kubuntu and they will not fix by themselves, as the bug system is broken.

A nasty bug in otherwise very nice looking Linux installation with lots of additional software on the DVD that could be installed once the system is self-healing (knows how to install reported bug fixes).

Anybody knows of a source for this information? Please assist me to help myself.

---

### Post by slakkie on 2010-01-02
Depends really.

If you have only a patch, you can apply the patch against the sources, create a debdiff:
[https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff](https://wiki.ubuntu.com/PackagingGuide/Recipes/Debdiff)

With the debdiff you can create a new package:
 [https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

If you want to the fixes to reach Ubuntu: [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

And normally Ubuntu provides the security updates via the -security repository (-updates also contains them most of the time). See also: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).  You can install them by upgrading:

```

sudo aptitude update
sudo aptitude safe-upgrade
# or with apt-get
sudo apt-get update
sudo apt-get upgrade

# and in certain cases you need (when packages are held back):
sudo aptitude full-upgrade
# or.. 
sudo apt-get dist-upgrade

```

Hope this answers your question :)

---

### Post by OldAlgis on 2010-01-02
> **slakkie said:**
> 
```

sudo apt-get update
sudo apt-get upgrade 
sudo apt-get dist-upgrade

```
Hope this answers your question :)

Many thanks, slakkie. Used all of the above.  As far as I can tell it all worked OK. During booting it shows now grub1.97~beta4, so there are changes.  Also, uname -a shows that the kernel is updated to 2.6.31-16-generic. AFAICS, the above "cooking receipe" worked!

Thanks a ton for saving an old man's sanity for another few months!

---

