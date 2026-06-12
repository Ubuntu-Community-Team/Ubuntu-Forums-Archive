---
title: "command"
date: 2010-06-10
forum: General Help
---

### Post by shipinomore on 2010-06-10
I am new to Ubuntu and looking for the terminal command to check the revision level or what is installed for Java and also to get the latest JRE for java installed.
I tried to install a tar pkg for Java 6u17 but not sure if worked.
thank you
Larry

---

### Post by tango_ninja on 2010-06-10
open a terminal window and type

```
java -version
```

This will tell you the current version of java installed.  If you don't have java installed you can do so via terminal (just make sure that the multiverse repository is enabled in System > Administration > Software Sources):

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

---

### Post by dino99 on 2010-06-10
goto: system admin synaptic, and search for "sun" on top, packages will be sorted, but check into synaptic repo, that canonical partner repo is activated, then update

---

