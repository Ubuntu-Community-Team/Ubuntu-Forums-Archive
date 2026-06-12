---
title: "Lets get rid of a bug"
date: 2010-10-19
forum: General Help
---

### Post by Bob65536 on 2010-10-19
I just upgraded to meerkat on my laptop and I also installed Live Mesh 2011 on my desktop. I am unable to view Windows shares from Ubuntu because of the live sign in assistant. I personally view this to be a major bug.

This is caused by a bug in samba that was fixed in July. There is a patch for this bug at [https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577). This issue is also fixed in samba 3.5.6.

I could just compile it for myself and fix it, but why not just fix it for everyone?

So my question is, how do we get this fixed? I know nothing about the politics of the Ubuntu project. Who do we need to email, txt, irc, call, blow, etc? And is there anything I can do to help fix this?

---

### Post by P4man on 2010-10-20
That bug fix will automatically find its way to your (our) systems sooner or later. 

Ubuntu is a distribution, its basically a combination of different apps and packages, like gnome, firefox, etc and or course, samba. All of these apps are constantly being worked on independently of ubuntu, bugs fixed, new features and versions introduced, as well as new bugs added :). The point of a distro is selecting a set of packages that work together and add some "glue".

The way ubuntu approaches that is keeping app versions stable within an ubuntu release (6 month). So not every new version of firefox, alsa or samba will automatically be included in your updates, that would be impossible to test. Basically when you upgrade to the next ubuntu release, you get newer versions of all those packages. 

But security and bug fixes are (usually) added, after they were tested and if the patches are available for the version of the app of package included in ubuntu. The patches are then applied, the app recompiled and the resulting binary made available through update manager. That is the task of the package maintainer(s). If you dont want to wait that long, you can find a PPA with a newer build of your app (samba in this case) or compile and install it yourself.

Or you can request it on launchpad, but filing  a bug report or contact the maintainers via the mailing list. Im not sure what the appropriate way is:
[http://packages.ubuntu.com/source/maverick/samba](http://packages.ubuntu.com/source/maverick/samba)

---

