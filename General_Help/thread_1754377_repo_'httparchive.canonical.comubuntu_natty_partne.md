---
title: "repo 'http://archive.canonical.com/ubuntu natty partner' ?"
date: 2011-05-10
forum: General Help
---

### Post by kenneth.koontz on 2011-05-10
While using add-apt-repository, I get:

```
$ sudo add-apt-repository "deb-src http://archive.canonical.com/ubuntu natty partner"
Error: 'deb-src http://archive.canonical.com/ubuntu natty partner' invalid
```

Is this repo really invalid? I want to use this repo to install Sun's JDK6. 

I am running ubuntu 11.4 64-bit server.

---

### Post by oldos2er on 2011-05-10
Remove the quote marks ```
sudo add-apt-repository deb-src http://archive.canonical.com/ubuntu natty partner
```

---

