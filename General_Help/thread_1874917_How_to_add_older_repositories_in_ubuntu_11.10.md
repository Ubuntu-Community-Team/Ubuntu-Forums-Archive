---
title: "How to add older repositories in ubuntu 11.10"
date: 2011-11-04
forum: General Help
---

### Post by vat with tux on 2011-11-04
Hi .... 

I come to know that some repositories which were there in ubuntu 11.04 are removed from 11.10 ...for example repository for "quanta plus" .

I want add repositories of ubuntu 11.04 to 11.10 ..... can anyone tell me that how can I do this???

---

### Post by notgary on 2011-11-10
Unfortunately repositories are tied to a particular distro, so when you upgrade from 11.04 to 11.10, if the maintainers of the thrid-party repositories haven't upgraded them to be compatible with the new distro, then unfortunately you're not going to be able to use them until they do.

The best thing to do would be to file a bug on the issue with the developers of Quanta Plus, which you can do here [http://quanta.sourceforge.net/bug.php](http://quanta.sourceforge.net/bug.php), and with the maintainers of any other repo that has stopped working.

---

### Post by de Bacon on 2011-11-20
I too want Quanta Plus since upgrading to 11.10 :(  I have come to depend on it and having it unavailable with this distribution is a problem for me!!

I hope I find out when this issue has been resolved, but I don't even know how to find that out!:confused:

---

### Post by cbowman57 on 2011-11-20
You can edit the sources.list & make an entry that has the repo or ppa & the previous version name.

---

