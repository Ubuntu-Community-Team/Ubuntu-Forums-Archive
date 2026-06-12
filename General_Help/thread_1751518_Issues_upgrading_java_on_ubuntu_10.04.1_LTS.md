---
title: "Issues upgrading java on ubuntu 10.04.1 LTS"
date: 2011-05-06
forum: General Help
---

### Post by Raider00321 on 2011-05-06
Hey there, Im having issues updating anf changing my preferences to which jvm i wish to use to. The problem is i used(guessing i did it incorrectly)

update-java-alternatives --install

And since then, i have not been able to get s jvm machine correctly selected
If it helps... this is what i get using 

sudo update-alternatives --config java

```


  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /etc/alternatives                          2         manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
 * 3            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

```And when checking for java using

java --version 

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm


Im really in a tight spot here, so if anyone can help me figure this out, but needs more information. just tell me what else you need. Any help would be greatly appreciated.

---

