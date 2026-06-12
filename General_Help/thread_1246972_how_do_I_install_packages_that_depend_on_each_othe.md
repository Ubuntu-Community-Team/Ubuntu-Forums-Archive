---
title: "how do I install packages that depend on each other?"
date: 2009-08-22
forum: General Help
---

### Post by shiggydiggy on 2009-08-22
like these ones...
[http://www.getdeb.net/search.php?keywords=audacity](http://www.getdeb.net/search.php?keywords=audacity)

---

### Post by fourthofjuly on 2009-08-22
> **shiggydiggy said:**
> like these ones...
[http://www.getdeb.net/search.php?keywords=audacity](http://www.getdeb.net/search.php?keywords=audacity)
if its a deb package, i suppose all dependencies will be resolved automatically...

in my experience its like trial and error, installing any program you will face number of dependencies, which when installed will have more dependencies and so on... quite a tedious task...

unless its there in the repos, don't bother installing ...

---

### Post by Hendrixski on 2009-08-22
umm, don't install audacity from some website

just click on Applications --> add/remove  and select audacity from the list and click apply


it installs itself. done :-D

---

### Post by Bonster on 2009-08-22
install the data deb 1st, then install the other one 2nd. It goes from dependency 1st in that order

---

### Post by shiggydiggy on 2009-08-22
> **Bonster said:**
> install the data deb 1st, then install the other one 2nd. It goes from dependency 1st in that order
tried that. like i said, they depend on one another
> **fourthofjuly said:**
> if its a deb package, i suppose all dependencies will be resolved automatically...

in my experience its like trial and error, installing any program you will face number of dependencies, which when installed will have more dependencies and so on... quite a tedious task...

unless its there in the repos, don't bother installing ...
> **Hendrixski said:**
> umm, don't install audacity from some website

just click on Applications --> add/remove  and select audacity from the list and click apply


it installs itself. done :-D
the repo version is 1.37 and really unstable. i want to install 1.38

it's probably easier just to install the windows version and run it with wine... something wrong there.

can i please get some real help?

---

### Post by michy99 on 2009-08-22
If you have all the .deb files in a directory together, then cd to that directory and```
sudo dpkg -i *.deb
```

---

### Post by oldos2er on 2009-08-22
Are you trying to install them with GDebi, or dpkg? I just now tried it with GDebi, installing the data deb first, and it worked.

---

### Post by shiggydiggy on 2009-08-23
idk... the one that comes with ubuntu

thanks michy99, that works!

---

