---
title: "apt equivalent of yum whatprovides"
date: 2012-04-06
forum: General Help
---

### Post by Alphamonkey on 2012-04-06
Hi, I am looking for an apt command that provides the same functionality of the yum -whatprovides command. I am trying to figure out "what provides" a package for a program that I am using. Thanks.

---

### Post by zombifier25 on 2012-04-06
There's apt-file and dpkg -S
However, apt-file is not installed by default, while dpkg -S will only show the packages already installed on your system.

---

### Post by Alphamonkey on 2012-04-06
Hi, thanks for the reply, I had already installed this last night prior to posting but i didn't think it was working. Turns out that the file I was looking for isn't in the standard repositories.

---

