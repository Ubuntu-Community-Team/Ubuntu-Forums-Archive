---
title: "Install JRE in Ubuntu 10.04"
date: 2012-07-28
forum: General Help
---

### Post by Ep1c0wl on 2012-07-28
[FONT="Arial"]Hello,

I have Ubuntu 10.04 LTS and wanted to get Java Runtime Environment for it. I went on the Java website and they only had the tar.gz file and no .deb file. If anybody can tell me how I can get JRE on Ubuntu it would be greatly appreciated.[/FONT]

---

### Post by Cheesemill on 2012-07-28
Run the following commands.
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by Karlchen on 2012-07-28
Hello, Ep1c0wl.

The instruction which I have been following since Lucid Lynx is this one : [https://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY](https://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY)

Kind regards,
Karl

---

### Post by Cheesemill on 2012-07-28
> **Karlchen said:**
> Hello, Ep1c0wl.

The instruction which I have been following since Lucid Lynx is this one : [https://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY](https://sites.google.com/site/easylinuxtipsproject/java#TOC-INSTALL-MANUALLY)

Kind regards,
KarlThe method that I posted is easier plus adding the PPA means that every time a Java update is released it will get upgraded automatically along with the rest of your system, no need to keep an eye out and update manually :)

---

### Post by Ep1c0wl on 2012-07-28
Cheesemill,

I have managed to get JRE7 up and running with the codes you have given me. Thanks,

**Ep1c0wl**

---

