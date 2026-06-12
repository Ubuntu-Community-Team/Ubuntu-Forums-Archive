---
title: "Debian"
date: 2006-06-22
forum: General Help
---

### Post by StingSlang on 2006-06-22
How is Ubuntu related to Debian?  

Can I run Debian programs on Ubuntu?

---

### Post by scxtt on 2006-06-22
yes, it uses debian packages ... so any *.deb packages will install ...

---

### Post by x64Jimbo on 2006-06-22
[QUOTE=scxtt]yes, it uses debian packages ... so any *.deb packages will install ...[/QUOTE]
Caution!
This practice is NOT recommended because it can break your package management system. Install Debian .deb's AT YOUR OWN RISK!

---

### Post by scxtt on 2006-06-22
riiiiiiiiiiiiiight ... even tho i've installed fglrx*.deb packages and synaptic tells me there is an update for them ...

i'm not saying you're wrong, or that it's flawless, but it works fine ... it's basically the same deal as rpm packages ...

---

### Post by aysiu on 2006-06-22
An individual .deb will usually be fine, but definitely don't make Debian repositories permanent parts of your /etc/apt/sources.list

---

### Post by mlind on 2006-06-22
If ubuntu is un-sync with debian stable/unstable or whatever, you can't install
debian's packages without running to dependency erros.

Currently it's very easy to rebuild Debian sid packages for Dapper because we
seem to be somewhat synced.

Ubuntu also sometimes customizes upsteam packages, adding
patches, integrations to own tools, and similar stuff.


/edit
damn typos

---

### Post by garyng on 2006-06-22
ubuntu is sort of a "derivative" of debian(use a snapshot at certain time as a base then customize) but in general NOT compatible with debian packages.

In fact, I notice that it is deviating from debian more and more.

---

