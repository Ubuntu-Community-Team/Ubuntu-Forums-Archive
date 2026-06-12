---
title: "'E:Type 'ntu-wine/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources."
date: 2011-04-11
forum: General Help
---

### Post by saioke on 2011-04-11
I'm having a problem updating or even running the software center. Each time I open either of them, I get an error stating "'E:Type 'ntu-wine/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list'" and the update manager or software center closes. This has just been happening a few days ago and I would like a fix for it. I'm using 11.04 beta 1 and my WINE version is the latest development release. Anyone know how to fix this error? I tried unchecking my WINE PPAs in sources but that don't seem to do any good.

---

### Post by 3rdalbum on 2011-04-11
Remove the file "/etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list":

```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
```

The first line of that file is not correct; all lines in the repository file must start with "deb", "deb-src" or a # (which means "ignore this line").

You'll also need to update your package list:

```
sudo apt-get update
```

---

### Post by saioke on 2011-04-11
> **3rdalbum said:**
> Remove the file "/etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list":

```
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-natty.list
```The first line of that file is not correct; all lines in the repository file must start with "deb", "deb-src" or a # (which means "ignore this line").

You'll also need to update your package list:

```
sudo apt-get update
```

Well, thank you very much! It worked. I'm still rather new to Ubuntu and Linux in general despite using it a few years back, so I'm still learning. Thanks for the help!

---

