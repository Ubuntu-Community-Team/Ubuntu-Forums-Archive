---
title: "Eclipse Crashing on every run.  Fresh Install from website."
date: 2010-11-11
forum: General Help
---

### Post by lukeaar on 2010-11-11
After getting sick of being behind the times using the repo version of eclipse, I apt-get removed it.  I then downloaded the latest version from the Eclipse website and now it crashes every time I run it with the following error:

JVM terminated. Exit code=1
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m
-jar /home/lukeaar/eclipse//plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /home/lukeaar/eclipse/eclipse
-name Eclipse
--launcher.library /home/lukeaar/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.1.R36x_v20100810/eclipse_1309.so
-startup /home/lukeaar/eclipse//plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-exitdata 527b0021
-product org.eclipse.epp.package.java.product
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m
-jar /home/lukeaar/eclipse//plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar 

How can I fix this?

---

