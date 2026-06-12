---
title: "NetBeans 6.9.1 performance ?!"
date: 2010-08-14
forum: General Help
---

### Post by saidbakr on 2010-08-14
Hi,
The NetBeans IDE - I use PHP dist. - is not accepted at all on Ubuntu 10.04. Some of our friends will claim this due to the JVM used or for some kind of settings. However, the final result is that NetBeans has important issue related with performance. The NetBeans seems to be unusable.

I think that netbeans should be released in a state better than of this state. I think NetBeans devellopers concentrates on MS Windows, because the performabe of netbeans on windows has no compariosn with those on Ubuntu.

I have both Komodo Edit and NetBeans and there is no comparison between them in the performance. By the way, I like NetBeans and its features, but its bad performance on Ubuntu shocks me!

---

### Post by tamashumi on 2010-08-24
Agree. The performance is really poor :(

---

### Post by robertu on 2010-08-30
I'm using netbeans php also and managed to get it working fast and stable. It is a matter of settings.

Please try:
- uninstall java openjdk [use synaptic]
- enable archive.canonical in synaptic
- install sun java 6 jre [use synaptic]

After this netbeans will work ok, but it is eating memory till the 512 mb ram is full, and netbeans will become verrrry slooooww. To solve this, change another setting:

Please try:
- open netbeans.conf (somewhere in your home / netbeans / etc directory)
- change the line with netbeans_default_options="-J-Xverify:none -J-client -J-Xss2m -J-Xms128m -J-Xmx1024m -J-XX:PermSize=256m -J-XX:MaxPermSize=512m -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-XX:+CMSPermGenSweepingEnabled -J-Dapple.laf.useScreenMenuBar=true -J-Dsun.java2d.noddraw=true"

Hope you become as happy as I am with Netbeans/Ubuntu :D

---

### Post by saidbakr on 2010-08-30
Hi, 
Thank you very much for the useful hint. I just adopted your configuration line
```

netbeans_default_options="-J-Xverify:none -J-client -J-Xss2m -J-Xms128m -J-Xmx1024m -J-XX:PermSize=256m -J-XX:MaxPermSize=512m -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-XX:+CMSPermGenSweepingEnabled -J-Dapple.laf.useScreenMenuBar=true -J-Dsun.java2d.noddraw=true"

```
I did not use any synaptic features, either install or uninstall, I just installed the latest jdk in my local folders and then I informed NetBeans to use its as jdk home from the configuration file regarded above:
```

netbeans_jdkhome="/home/admin/MyProgs/jdk1.6.0_21"

```

---

