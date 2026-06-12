---
title: "add packages.debian.org to ubuntu repositories for gretl"
date: 2011-10-01
forum: General Help
---

### Post by pythonscript on 2011-10-01
How do I add packages.debian.org to my sources.list so I can install the latest version of gretl for Ubuntu 11.04 (since the default version is broken). The gretl site says that this is the repository: [http://packages.debian.org/gretl](http://packages.debian.org/gretl) so should I add that to /etc/apt/sources.list file?

I know how to edit the file, I know how to update my system and install packages from the terminal, etc. but I'm stuck on this specific repository, since it's not a standard PPA or an ubuntu repo. 

Thanks!

---

### Post by mikewhatever on 2011-10-01
The site ([http://gretl.sourceforge.net/](http://gretl.sourceforge.net/)) does not provide the repository, nor does it suggest adding anything to the sources.list. The link you posted it not a repository, it simply leads to gretti 1.9.5 for Debian which you are supposed to download and install.

---

### Post by dcstar on 2011-10-02
As well, anyone adding Debian repositories to their Ubuntu systems is guaranteed to break Ubuntu in one way or another.

---

### Post by pythonscript on 2011-10-09
Thanks for the help; I realised that I needed a different package than gretl, so I didn't need to trouble myself with all of it anyway.

---

### Post by TBeholder on 2012-09-13
gretl aside, let's add one helpful answer just for completeness. :)

Do it [per instruction on help.ubuntu.com](https://help.ubuntu.com/community/Repositories/Ubuntu):
The apt line is "**deb [http://ftp.debian.org/debian](http://ftp.debian.org/debian) squeeze main**"
[Their GPG key was changed, so get the new one - "**473041FA**"](http://www.debian.org/News/2011/20110209)

> **dcstar said:**
> As well, anyone adding Debian repositories to their Ubuntu systems is guaranteed to break Ubuntu in one way or another. As opposed to?..
E.g. [xpdf is broken in Ubuntu for more than half a year]("https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/943195").
I got a *non-crashing* xpdf via downgrading to 3.02-12+squeeze1 from there (with poppler5 in tow).
Aye, still disabled the repository until the next case, because there are 25 other updates of unknown compatibility, after forcing version and installing.
Obviously it would also work completely clean most soft running on Python or Java (and there's a lot).

---

