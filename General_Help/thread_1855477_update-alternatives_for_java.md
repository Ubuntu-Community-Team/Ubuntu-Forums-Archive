---
title: "update-alternatives for java"
date: 2011-10-06
forum: General Help
---

### Post by _nikolaos on 2011-10-06
I need to install an older version of java (Java 1.5) in my ubuntu machine, and make it default java VM in spite of my current installation.

This is what results from executing update-alternatives:

~$ update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.

I am no sure what my next step should be. The worse is that I can find no repository or anything similar in the internet that provides a Java 1.5 VM. I am addicted to use "apt-get install" for everything, so I am having a hard time understanding the process.

I suppose that "update-alternatives --install" is probably what I will do, but I need help about how.

---

### Post by Krytarik on 2011-10-06
Try this:
```
sudo update-alternatives --install /usr/bin/java java /<path-to-your-java-dir>/jre/bin/java 1000
sudo update-alternatives --config java
```If that isn't enough, try this:

[http://blogs.oracle.com/pc/entry/easy_way_to_set_your](http://blogs.oracle.com/pc/entry/easy_way_to_set_your)

Regards.

---

