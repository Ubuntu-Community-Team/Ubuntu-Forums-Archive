---
title: "TeX-live repository"
date: 2006-06-20
forum: General Help
---

### Post by Nonno Bassotto on 2006-06-20
Since TeTeX will be no more mantained I'm planning to pass to TeX-live, but it isn't in the repositories yet. Is it safe to use the debian repository indicated [here]("http://www.tug.org/texlive/debian")? In general, what problem can arise in using external Debian repositories?

---

### Post by hod139 on 2006-06-20
I'm sure that TeTex will be fine for a while, and eventually the Ubuntu developers will migrate to TeX Live.  Mixing debian packages can be dangerous.

---

### Post by Nonno Bassotto on 2006-06-21
I wouldn't care, but the package babel has a bug. The bug is the following: if you use babel together with the class amsart, your language is shown in the headers near the author name or the title. It is a known bug, and it is corrected in the current version of babel, which is 3.8g. The version in the repos is 3.8d.

I'd try to manually upgrade the babel package only, but it seems complicated. The package babel seems to be composed by a lot of files, and I don't know which files I'd have to put in a local texmf. This is why I was thinking to upgrade the whole TeX package.

---

### Post by hod139 on 2006-06-21
Looks like you aren't alone:
[http://ubuntuforums.org/showthread.php?t=184231](http://ubuntuforums.org/showthread.php?t=184231)

Anyways, hopefully one of these howto's will help you:
[http://ubuntuforums.org/showthread.php?t=131507](http://ubuntuforums.org/showthread.php?t=131507)
[http://ubuntuforums.org/showthread.php?p=807144](http://ubuntuforums.org/showthread.php?p=807144)
[http://www.ubuntuforums.org/showthread.php?t=148954](http://www.ubuntuforums.org/showthread.php?t=148954)

---

