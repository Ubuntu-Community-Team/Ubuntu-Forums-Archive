---
title: "error: no alternatives for xulrunner-1.9-javaplugin.so."
date: 2012-08-22
forum: General Help
---

### Post by jiapei100 on 2012-08-22
Hi, all:

Environment: Ubuntu 12.04 + [Oracle Java SE 7u6 from PPA]("https://launchpad.net/~webupd8team/+archive/java")
After the installation (strictly following [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html) ), I got the popular error messages:

> peijia@peijia-GA-870A-UD3:/etc/alternatives$ sudo update-java-alternatives -s java-7-oracle
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-7-oracle/jre/bin/jexec for jexec not registered, not setting.
update-alternatives: error: alternative /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.



Any solutions to removing the above errors?


Best Regards
Pei

---

### Post by otinho on 2012-11-07
Probably you already found it, but i'll leave it anyway so other people can find it:
> if 32bit - sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so 1
if 32bit - sudo update-alternatives --set mozilla-javaplugin.so /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so
if 64bit - sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-7-oracle/jre/lib/amd64/libnpjp2.so 1
if 64bit - sudo update-alternatives --set mozilla-javaplugin.so /usr/lib/jvm/java-7-oracle/jre/lib/amd64/libnpjp2.so
taken from here; [https://docs.google.com/document/d/1DzjvNgiF8OMUD0L6LdvOkvDcc6wYIk1iPFCkoW2pPf4/edit](https://docs.google.com/document/d/1DzjvNgiF8OMUD0L6LdvOkvDcc6wYIk1iPFCkoW2pPf4/edit)
Tried it, worked on my environment (xubuntu 12.10)

---

