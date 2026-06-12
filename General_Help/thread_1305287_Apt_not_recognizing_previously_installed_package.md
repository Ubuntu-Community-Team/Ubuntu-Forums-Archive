---
title: "Apt not recognizing previously installed package"
date: 2009-10-29
forum: General Help
---

### Post by lilbill on 2009-10-29
Hi all,
I'm just getting my system back in shape after a clean karmic install.  I've installed a package from the developers , TexLive 2008, since the version in the repos is 2007.  Now, when I go to install another package, Kile, using apt-get it is attempting to install TexLive again since it is a Kile dependency.

Is there a way to prevent this behavior?  I'd really like to get the Kile/KDE stuff set up without downloading about 1GB worth of files for TexLive 2007.

Thanks!

P.S. Karmic has some great performance fixes which I've noticed already.

---

### Post by Rocket2DMn on 2009-10-29
Both texlive and kile are in the Karmic repos - have you enabled the Universe repository (which is where kile is)?

---

### Post by lilbill on 2009-10-29
I've found them both in the repos...but the problem that I'm having is that I have TexLive2008 installed (not via apt) and am now trying to install Kile through apt, but apt is trying to reinstall TexLive from the repos.

So, I'm looking for a way to either:
1.  Make apt recognize that TexLive is installed
2.  Make apt forgo installing some of Kile's dependencies (namely TexLive).

Sorry that I was unclear in my first post and thanks for the reply!

---

### Post by lilbill on 2009-10-29
Bump

---

### Post by dnova on 2009-10-31
Try creating a "dummy" texlive2007 package. Some info here: [http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/](http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/)

---

