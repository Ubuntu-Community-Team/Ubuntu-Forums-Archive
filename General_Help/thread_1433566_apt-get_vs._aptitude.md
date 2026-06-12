---
title: "apt-get vs. aptitude"
date: 2010-03-19
forum: General Help
---

### Post by derekeverett on 2010-03-19
If my understanding is correct, is aptitude not a better way to install software from the command line than apt-get is?

aptitude installs all recommended dependencies correct? 

Just looking for some input here.

---

### Post by wojox on 2010-03-19
Well apt-get and aptitude have become almost identical for managing packages. The only major difference is that aptitude will automatically install "recommended" packages, while apt-get only installs "depended" packages. So with aptitude you might get a bit more bulk/features.

---

### Post by 3rdalbum on 2010-03-19
Aptitude knows what packages have been pulled in as dependencies, and will remove the dependencies when you remove the original package (unless they are dependencies of something else as well).

However, Apt-Get keeps track of the same thing these days, and can remove these old dependencies using sudo apt-get autoremove.

---

### Post by Brv on 2010-03-19
You can also run aptitude from the command line. For example
aptitude update
aptitude upgrade
aptitude dist-upgrade

Aptitude is said to deal with dependencies better than apt-get. For example, say you install a package which automatically installs some library packages because it depends on them. When you remove this package with apt-get, it won't remove the libraries this package installed, although they aren't used anymore.
When you install that package with aptitude and remove it with aptitude, aptitude 'detects' that those library packages aren't used anymore and will therefore automatically remove them.
I myself switched from apt-get to aptitude.

[_[COLOR=DarkRed]http://www.psychocats.net/ubuntu/aptitude[/COLOR]_]("http://www.psychocats.net/ubuntu/aptitude")

~Brv

---

