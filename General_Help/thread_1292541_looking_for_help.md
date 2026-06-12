---
title: "looking for help"
date: 2009-10-16
forum: General Help
---

### Post by weirdo-espionage on 2009-10-16
i try to install basic application (lynx) into my ubuntu server..
but seem it fail and i don't know why..

the message after i enter the apt-get command is:

[B]P[B]ackage lynx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted or only available from another source
E: Package lynx has no installation candidate[/B]
[/B]
some time it like this
**E:  Couldn't find package bla bla**

---

### Post by lindsay7 on 2009-10-16
[http://www.softlookup.com/download.asp?id=40190](http://www.softlookup.com/download.asp?id=40190)

---

### Post by hal10000 on 2009-10-16
on my system i had to install lynx-cur, because lynx is outdated

---

### Post by weirdo-espionage on 2009-10-16
apt-get will download application from the server if could not find it.. did i'm right?

---

### Post by hal10000 on 2009-10-16
[COLOR="Red"]apt-get install *packagename*[/COLOR] downloads the deb package if it's not already in your cache directory **and **installs it.

You should perform a [COLOR="Red"]sudo apt-get update[/COLOR] before installing a package to refresh your package list

---

### Post by Baelus on 2009-10-16
> **hal10000 said:**
> [COLOR="Red"]apt-get install *packagename*[/COLOR] downloads the deb package if it's not already in your cache directory **and **installs it.

You should perform a [COLOR="Red"]sudo apt-get update[/COLOR] before installing a package to refresh your package list

Good advice. Run sudo apt-get update before installing packages.

You can also use this:

```
apt-cache search *package-name*
```

That will give you a list of packages that relate to the search term.

There may be a lot of them, so you can try this too:

```
apt-cache search *package-name* |grep *package-nam*e
```

That should give you a more pertinent list.

---

