---
title: "Stop aksing for CD on apt-get package installs?"
date: 2006-04-03
forum: General Help
---

### Post by behemothaur on 2006-04-03
I have seen the answer to this before and had it working on my last build - what do I need to change so that my current build will default to sources.list for packages?

I have changed the sources.list so that all the repositories I want are checked on an update and have updated apt-get.

Thanks...

---

### Post by frodon on 2006-04-03
remove the CD lines in your sources.list file and the system will not ask you anymore for the CD.
Post your source.list file here if you have problems : ```
sudo gedit /etc/apt/sources.list
```

---

### Post by behemothaur on 2006-04-05
[QUOTE=frodon]remove the CD lines in your sources.list file and the system will not ask you anymore for the CD.
Post your source.list file here if you have problems : ```
sudo gedit /etc/apt/sources.list
```[/QUOTE]

Thanks! Never noticed that CD line at the top of the sources.list before, I have always installed ubuntu from scratch, this time I am using the vmware image...

---

