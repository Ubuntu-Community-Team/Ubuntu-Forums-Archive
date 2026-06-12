---
title: "convert ebuild in deb"
date: 2006-02-28
forum: General Help
---

### Post by Josef K. on 2006-02-28
is there anything like alien to convert a gentoo package in a deb one?

---

### Post by Xian on 2006-03-01
[QUOTE=Josef K.]is there anything like alien to convert a gentoo package in a deb one?[/QUOTE]

Alien converts an actual package (such as a binary RPM format) into a deb file, but Gentoo is comprised of E-builds which are only scripts that are run to compile a source package locally. Which is merely to say that alien needs an real package to convert instead of a script. What package are you wanting to convert??

---

### Post by hw-tph on 2006-03-01
In addition to what Xian wrote above, dh_make and related tools are very good for building Debian packages from source.


Håkan

---

### Post by Josef K. on 2006-03-02
[this one]("http://kde-apps.org/content/show.php?content=35624")
since is the only version of kerry I founded

---

