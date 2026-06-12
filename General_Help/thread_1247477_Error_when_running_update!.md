---
title: "Error when running update!"
date: 2009-08-23
forum: General Help
---

### Post by danscali on 2009-08-23
Lately I ran into this error. Does anyone know how to fix this? I'm running 9.04 version

"W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) jaunty-arakhne Release: The following signatures were invalid: KEYEXPIRED 1250412934 KEYEXPIRED 1250412934 KEYEXPIRED 1250412934"

Thanks for your help!

---

### Post by 3rdalbum on 2009-08-23
It's not an error, it's a warning; you can install packages from the repository even though the GPG key is not available (or even if it has expired).

Maybe you should have a look at the Tuxfamily website to find out the GPG key to add for the repository.

---

### Post by danscali on 2009-08-24
Could you show me the link to the Tux website thing?

---

### Post by P4man on 2009-08-24
why are you downloading from their repo's? A quick glance at what it contains seems woefully out of date.

---

### Post by danscali on 2009-08-27
It was like that when I installed the Ubuntu 9.04. Could you show me how to fix it?

---

### Post by P4man on 2009-08-27
You are probably best off making a new sources.list

here is a neat site to help you make one:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Select country and version.
in "Ubuntu Branches" select everything
in "Ubuntu Updates" select the first four 
in "Ubuntu Partner Repos" select the first one
in "3rd Parties Repos" you normally dont need to select anything, unless you are running one of those apps and you want to have a newer version than what is available in the official repo's. If in doubt, no need to select anything (not that it would hurt). perhaps "Medibuntu" is worth selecting though.

Then click generate list. Copy paste the result over your existing sources.list. To edit that list:

```
gksudo gedit /etc/apt/sources.list
```

---

