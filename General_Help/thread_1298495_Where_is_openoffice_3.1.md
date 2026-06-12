---
title: "Where is openoffice 3.1"
date: 2009-10-22
forum: General Help
---

### Post by JigglyWiggly_ on 2009-10-22
So I am using xubuntu 8.04 on an old laptop.
Anyway, I installed openoffice from the respitory, only to find it's 2.4, while is old old old.

So I uinstalled it, then went to their website and installed the latest. It's a deb.tar.gz
I just unextracted it and went to the DEB folder and did
sudo apt-get install *deb

It installed, but where is it? It's not in the applications > office. Is this because I am using xubuntu? Help is appreciated :)

---

### Post by winotree on 2009-10-22
> **JigglyWiggly_ said:**
> So I am using xubuntu 8.04 on an old laptop.
Anyway, I installed openoffice from the respitory, only to find it's 2.4, while is old old old.

So I uinstalled it, then went to their website and installed the latest. It's a deb.tar.gz
I just unextracted it and went to the DEB folder and did
sudo apt-get install *deb

It installed, but where is it? It's not in the applications > office. Is this because I am using xubuntu? Help is appreciated :)
I'm not sure where it is -- you might be able to run it via a terminal, but I just looked and version 3.1.1 *is *available in the [my] repositories.  ;)

EDIT - rephrased my post after re-reading OP post

EDIT - I'm using the standard repositories -- first four ticked in Software Sources

---

### Post by JigglyWiggly_ on 2009-10-23
Maybe the old one is showing up because I am on xubuntu 8.04? This is getting to be stupid tbh.

And yeah I looked at my sources.list file

---

### Post by P4man on 2009-10-23
Its how ubuntu works. They do not update the programs after a release, they keep m stable, only offering bugfixes.  At least in the official repo's. Read this:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Its not silly, its quit logical. You cant maintain 2 releases per year if you are also going to support all updates of all programs in them too. It would be a nightmare. 

Anyway, either upgrade your ubuntu or install OO from another source than the official repo.

---

