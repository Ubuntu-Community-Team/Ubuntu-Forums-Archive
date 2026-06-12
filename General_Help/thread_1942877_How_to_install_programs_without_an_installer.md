---
title: "How to install programs without an installer"
date: 2012-03-18
forum: General Help
---

### Post by alkal0id on 2012-03-18
I downloaded JDK 7 from here:
[http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html)
but they didn't have any .deb files so I just downloaded a tar.gz archive. I extracted it onto my desktop. Right now to use the compiler, I have to tell the terminal the full directory that javac is located in (i.e. ~/Desktop/jdk/bin/javac). Where was I supposed to extract the archive to?

EDIT: To install jdk properly, I followed this guide:
[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)
which worked. I regularly encounter this situation though, where there is no .deb or .sh (or whatever) installer, just a .tar.gz archive of directories with no instructions on how to install the software. When this happens, I usually resort to looking for it in synaptic package manager but more often than not, its not in there because when a program is in the repositories, I just install it with the command line.

---

### Post by 2F4U on 2012-03-18
Fortunately, the process of installing it is pretty well documented:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

---

