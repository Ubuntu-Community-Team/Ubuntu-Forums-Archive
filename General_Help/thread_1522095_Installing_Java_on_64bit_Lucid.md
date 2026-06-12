---
title: "Installing Java on 64bit Lucid"
date: 2010-07-01
forum: General Help
---

### Post by tripower on 2010-07-01
I followed this link:

[http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)


But the link for making the link for the java plugin and Firefox doesn't work. Any help please.

---

### Post by chrisccoulson on 2010-07-01
> **tripower said:**
> I followed this link:

[http://wojox.homelinux.org/?p=78](http://wojox.homelinux.org/?p=78)


But the link for making the link for the java plugin and Firefox doesn't work. Any help please.

The suggestion to make the link is somewhat bogus. It tells you to link the OJI based Java plugin in to the mozilla plugins folder - this won't ever work on Lucid though, as Firefox 3.6 doesn't support OJI anymore.

In any case, that step isn't needed. Java plugins are registered with the alternatives system, and the sun-java6-plugin package already provide a Java plugin for Firefox (/usr/lib/mozilla/plugins/javaplugin.so). If you want to make sure it points to the Sun Java plugin, just run "sudo update-alternatives --set mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so" 

Also, the output of "java -version" in the guide is no confirmation that the Sun Java runtime is installed properly - the output is showing he is using the openjdk-6 package. The author should have selected the Sun Java binary by running "sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java" first, to confirm that it is working correctly

---

