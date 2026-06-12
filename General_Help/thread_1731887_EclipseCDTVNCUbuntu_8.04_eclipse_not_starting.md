---
title: "EclipseCDT/VNC/Ubuntu 8.04 eclipse not starting"
date: 2011-04-17
forum: General Help
---

### Post by Shwick2 on 2011-04-17
I'm not sure if I set this up properly.  I want to start Eclipse CDT on my Ubuntu 8.04 install using X11 through VNC.

When I try to run eclipse through vnc viewer command line using ./eclipse it hangs for a few seconds then fails.  No error message is output on the command line.

Is there a startup error log or some place I can look to find out what's happening? Or am I doing this wrong?

---

### Post by Shwick2 on 2011-04-18
Ok I've verified that the problem is eclipse.

Is there some kind of version clash here?

desktop: ubuntu desktop 8.04 lts
kernel: 2.6.24-22-generic
CDT 7.0.2 for Eclipse Helios
jre1.6.0_24

When I do ./eclipse it just hangs for a few seconds and I get no error at all. I also don't know if there is a log file that would store startup errors. Is anyone familiar with this kind of problem?

My eclipse.ini is the default file with the -vm argument added,

```

-startup
plugins/org.eclipse.equinox.launcher_1.1.1.R36x_v20101122_1400.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.2.R36x_v20101019_1345
-product
org.eclipse.epp.package.cpp.product
--launcher.defaultAction
openFile
-showsplash
org.eclipse.platform
--launcher.XXMaxPermSize
256m
--launcher.defaultAction
openFile
-vm
/home/shwick/ghostDev/java/jre1.6.0_24/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx384m

```

---

### Post by Shwick2 on 2011-04-18
I booted into my ubuntu 10 partition on my windows machine, did the exact same thing installing eclipse 3.6 helios with jre 1.6 and eclipse ran fine.

Right now I need to know how to get a description of the error that is occurring even though it is not output to the command line or ubuntu's system log /var/log/messages.

./eclipse just hangs and then returns to the command line

---

