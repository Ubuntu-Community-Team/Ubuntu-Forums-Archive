---
title: "Setting Proxy"
date: 2010-07-27
forum: General Help
---

### Post by powertower on 2010-07-27
Can someone tell me how to set default proxy settings for java? Windows allows you to do this in control panel-java. Does Ubuntu have something similar? Its causing my java apps to time out and Firefox to freeze.

Ubuntu 10.04

java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

---

### Post by the_olo on 2010-08-12
See the file [FONT="Courier New"]/etc/java-6-openjdk/net.properties[/FONT] - you cna place the default values for [FONT="Courier New"]http.proxyHost[/FONT], [FONT="Courier New"]http.proxyPort[/FONT] and other Java system properties over there.

If you're not using the official Ubuntu's OpenJDK package, then [FONT="Courier New"]/etc/java-6-openjdk[/FONT] may not be present.

In such a case, [FONT="Courier New"]net.properties[/FONT] will be present in the [FONT="Courier New"]jre/lib[/FONT] subdirectory of your JDK installation.

---

### Post by efflandt on 2010-08-12
I don't know about java in particular, but you can make general proxy settings in System > Preferences > Network Proxy.  And you can set that "System Wide" (so it will work for all browsers, etc.).

---

