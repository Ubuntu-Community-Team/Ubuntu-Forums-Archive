---
title: "Can't download OpenJDK"
date: 2010-09-01
forum: General Help
---

### Post by tt33l3r on 2010-09-01
Whenever I try to install OpenJDK the download fails. Is there anywhere else I can get it from or another way to fix this?

---

### Post by fjsimpkins on 2010-09-01
> **tt33l3r said:**
> Whenever I try to install OpenJDK the download fails. Is there anywhere else I can get it from or another way to fix this?

try this in terminal

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre

---

