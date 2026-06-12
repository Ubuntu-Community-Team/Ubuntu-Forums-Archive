---
title: "Could not create the Java virtual machine"
date: 2011-04-13
forum: General Help
---

### Post by ktneely on 2011-04-13
I have Sun's java installed but when I attempt to run it, I get the "could not create the Java virtual machine" error message.  Any ideas how to fix this?

```

ktneely@ktneely-t400:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

ktneely@ktneely-t400:~$ java --version
Unrecognized option: --version
Could not create the Java virtual machine.

ktneely@ktneely-t400:~$ sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.

```

thanks!

---

### Post by sanderj on 2011-04-13
"java --version" is incorrect. Try "java -version" or "java" instead.

HTH

---

### Post by ktneely on 2011-04-16
You're right, that works.  Hmm, I still cannot launch the application I'm trying to launch, but it's likely an incompatibility with the particular app. 

```
ktneely@ktneely-t400:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)
```


Thanks sanderj!

---

