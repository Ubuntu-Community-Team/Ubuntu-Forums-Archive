---
title: "Installing Eclipse and Android"
date: 2012-05-16
forum: General Help
---

### Post by rewritw on 2012-05-16
Hi,

I'm running Ubuntu 12.04 x86_64; 

Now my problem is I can't seem to get Eclipse to install ADT (Android Development Tools). I've done it one Lucid before, but can't get it to work on Precise. I have Eclipse 3.7 in both 32-bit and 64-bit. If I install 64-bit (/opt/eclipse), I can run eclipse and it works fine, but ADT won't install. If I try the 32-bit Eclipse, it just won't open. I get this error instead:
> [SIZE="1"]JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m
-jar /home/soshite/Downloads/eclipse/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/soshite/Downloads/eclipse/eclipse/eclipse
-name Eclipse
--launcher.library /home/soshite/Downloads/eclipse/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.100.v20110505/eclipse_1407.so
-startup /home/soshite/Downloads/eclipse/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar
--launcher.overrideVmargs
-exitdata 1210006
-product org.eclipse.epp.package.java.product
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m
-jar /home/soshite/Downloads/eclipse/eclipse//plugins/org.eclipse.equinox.launcher_1.2.0.v20110502.jar [/SIZE]

Checking java version:
> [size=1]% java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

% /usr/bin/java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu2)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

% which java
/usr/bin/java[/size]

After some research, I need the package "ia32-libs" and "sun-java6-jdk". I was able to install ia32-libs but sun-java6-jdk doesn't seem to be available. If I could at least get the 32-bit one to run and run with android that'd be fine, but it doesn't want to open. I've tried changing the directory a couple times. Right now it's in Downloads because I've been swapping around a lot between 32-bit and 64-bit.

 Thanks. Any help appreciated.

---

### Post by rai4shu2 on 2012-05-16
If you want Sun Java, you'll need [OAB]("https://github.com/flexiondotorg/oab-java6"). It's a pain, but I don't see an alternative.

---

