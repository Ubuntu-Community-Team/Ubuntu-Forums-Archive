---
title: "Enabled multiverse, still can't get Java 6?"
date: 2010-12-20
forum: General Help
---

### Post by cats4gold on 2010-12-20
As per [this guide,]("https://help.ubuntu.com/community/JavaInstallation") I've enabled the multiverse source in /etc/apt/sources.list. However, using "sudo apt-get install sun-java6-bin" yields the same result:

```
cats4gold@laptop:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sun-java6-bin

```

As far as I could tell, multiverse was enabled by default, so I don't see what's wrong here. Any advice?

---

### Post by PRC09 on 2010-12-20
I believe those instructions are outdated...If using 10.10 Maverick see....

[http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

---

### Post by cats4gold on 2010-12-20
> **PRC09 said:**
> I believe those instructions are outdated...If using 10.10 Maverick see....

[http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

Thank you, you are super-awesome. :D

---

### Post by PRC09 on 2010-12-20
You are welcome.......

---

