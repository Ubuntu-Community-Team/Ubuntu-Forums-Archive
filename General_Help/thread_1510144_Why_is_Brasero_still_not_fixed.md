---
title: "Why is Brasero still not fixed?"
date: 2010-06-15
forum: General Help
---

### Post by timgood on 2010-06-15
Brasero worked very well in 9.10, but in Lucid it fails to allow audio CD copying with an uninformative error message. This is not down to Brasero, apparently, but cdrdao. This bug has been reported since Lucid was in beta. 

I am trying to persuade individuals and companies to adopt Open Source solutions in general and Ubuntu in particular, but I am finding it that much harder when an apparently simple bug with a known fix is not solved and implemented in a LTS release. 

I know that cd copying is available from the command line and I am happy to do that. My customers will not be. Let's get this sorted!

---

### Post by Linuxforall on 2010-06-15
> **timgood said:**
> Brasero worked very well in 9.10, but in Lucid it fails to allow audio CD copying with an uninformative error message. This is not down to Brasero, apparently, but cdrdao. This bug has been reported since Lucid was in beta. 

I am trying to persuade individuals and companies to adopt Open Source solutions in general and Ubuntu in particular, but I am finding it that much harder when an apparently simple bug with a known fix is not solved and implemented in a LTS release. 

I know that cd copying is available from the command line and I am happy to do that. My customers will not be. Let's get this sorted!

Brasero is also unable to burn iso image, gnomebaker otoh works with everything so give that a try for now.

---

### Post by philinux on 2010-06-15
> **timgood said:**
> Brasero worked very well in 9.10, but in Lucid it fails to allow audio CD copying with an uninformative error message. This is not down to Brasero, apparently, but cdrdao. This bug has been reported since Lucid was in beta. 



[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696) There are a few dups of this too.
Looks like a fix is in proposed.
[http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg11172.html](http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg11172.html)

---

### Post by timgood on 2010-06-15
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696) There are a few dups of this too.
Looks like a fix is in proposed.
[http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg11172.html](http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg11172.html)

Looks like they've marked the fix as non-urgent - but I don't believe this is the fix for audio cd copying, but audio cd creation.

Renzo Bagnati has packaged a new version of Brasero and cdrdao which solves this problem, over 2 weeks ago. Why has the fix not been released?

---

### Post by philinux on 2010-06-15
> **timgood said:**
> Looks like they've marked the fix as non-urgent - but I don't believe this is the fix for audio cd copying, but audio cd creation.

Renzo Bagnati has packaged a new version of Brasero and cdrdao which solves this problem, over 2 weeks ago. Why has the fix not been released?

It might be stuck in proposed.
[http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/maillist.html](http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/maillist.html)

---

