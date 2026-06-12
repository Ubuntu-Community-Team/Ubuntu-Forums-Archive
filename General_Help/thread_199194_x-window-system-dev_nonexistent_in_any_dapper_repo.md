---
title: "x-window-system-dev nonexistent in any dapper repo"
date: 2006-06-18
forum: General Help
---

### Post by keithjr on 2006-06-18
Hi all,
  I've been trying for a while now to [install and configure WineX]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Wine&back=HOWTO+INDEX+Wine") for my dapper install, and have hit a brick wall very quickly.  The installation depends on a package called x-window-system-dev, which I've been searching high and low to find.  As far as I can tell this package, which is a developement package supported under breezy, [was found in the security repo]("http://packages.ubuntulinux.org/breezy/x11/x-window-system-dev") (why???).  However, there is no breezy backport repository for the security packages.  I've enabled all the others, but I can't find any page that'll tell me where this package is, as it must clearly be elsewhere.  So, how can I get this very important package?  

As far as I can tell, this package is just a collection of other small dev packages.  Do I have to install these all one by one?  Why isn't this package supported anymore?  Just downloading the deb file doesn't work either since it has so many dependencies.  Yes, I've run apt-get update, before you ask.

---

### Post by jtull89 on 2006-08-06
It might be under xorg-dev, but I'm not sure.

---

