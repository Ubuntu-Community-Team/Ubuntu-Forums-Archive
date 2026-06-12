---
title: "Is it possible to patch source then install normally?"
date: 2009-11-17
forum: General Help
---

### Post by shoeman22 on 2009-11-17
Is it possible to get the source of a package from apt-get source apply some patches to the code, and then install it just like the package from the repo would normally be installed, except with the patches in place?

The reason I ask is I've needed to apply some patches to MythTV which aren't even in trunk yet, much less the ubuntu repos, in order for my HD-PVR to work as it should.  I've been able to compile ok and everything works, but when I do it this way, I miss out on all the extra stuff that is added by the package, such as the menu shortcuts, the startup scripts, good defaults, etc. that'd I'd like to have if I can.

It's almost like I just need to roll up the directory apt-get source mythtv gave me back into a package after applying the patches, but I'm not sure how to do that.

---

### Post by luctor on 2009-11-17
short answer : checkinstall
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
It creates deb packages from source

---

### Post by shoeman22 on 2009-11-17
I've used checkinstall before for installing newer versions of PHP, but I may have to give it a try for this as well.  I was under the impression it just kept track of what make install was already going to do right?  A good move for sure, but I'm not sure if that's all I need from it.

It did lead me to the packaging link though, so I may give that a go later as well.

Thanks for the help.

---

