---
title: "tzdata package dependency error"
date: 2010-10-12
forum: General Help
---

### Post by Geryon on 2010-10-12
I am trying to install 'default-jdk' under Maverick which is producing a dependency error.  After drilling down it comes down to this:

The following packages have unmet dependencies:
 tzdata-java : Depends: tzdata (= 2010l-1) but 2010m-0ubuntu0.10.04 is to be installed
E: Broken packages

I checked my apt sources and I am pulling down from us.archive.ubuntu.com/ubuntu which I am assuming has the latest packages. 

I upgraded this install from a fresh install of Lucid and this is the first time I am trying to install the jre on here.  I upgrade via 'do-release-upgrade'.

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

# uname -a
Linux lanfear 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

The version of tzdata I have is indeed "2010m-0ubuntu0.10.04" which I is from Lucid.  Running an apt-cache search shows that the latest version is also "Version: 2010m-0ubuntu0.10.04".

Now via this page 'http://packages.ubuntu.com/search?keywords=tzdata' it shows that the version for maverick should be '2010l-1'.  I've made sure to update my apt sources and it's still return the lucid version of tzdata.  I've confirmed that the version in the sources list is indeed set to maverick as well.  I have cleared out the cache 'rm -rf /var/cache/apt' and re-ran everything to no avail.  

So aside from downloading the package manually and installing it, what can I do to get around this?

---

### Post by Geryon on 2010-10-12
Actually, I'm not looking close enough.  It's saying it needs '2010l' or higher and '2010m' is indeed higher.  It's definitely 'l' and not a '1' in there.  

I don't know why I didn't check this earlier.  This is what I am pulling down from the repository.  I cleared all my apt cache, did an update and this is what I received from us.archive.ubuntu.com.

Package: tzdata-java
Priority: optional
Section: libs
Installed-Size: 1916
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: all
Source: tzdata
Version: 2010l-1
Depends: tzdata (= 2010l-1)
Filename: pool/main/t/tzdata/tzdata-java_2010l-1_all.deb
<snip>

Here's the contents of my 'sources.list':

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse


Looks pretty standard...  Any thoughts?

---

