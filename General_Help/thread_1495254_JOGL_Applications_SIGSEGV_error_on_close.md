---
title: "JOGL Applications SIGSEGV error on close"
date: 2010-05-27
forum: General Help
---

### Post by js911 on 2010-05-27
I've been developing OpenGL applications using Java + JOGL for some time now, and I recently updated to Ubuntu 10.04. The programs themselves run just fine, but they often (~75% of the time) report an error when I close them. For example:

#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fbbf201bc98, pid=2027, tid=140445215057680
#
# JRE version: 6.0_20-b02
# Java VM: Java HotSpot(TM) 64-Bit Server VM (16.3-b01 mixed mode linux-amd64 )
# Problematic frame:
# C  [libX11.so.6+0x37c98]  XQueryExtension+0x28
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#

I did not have this problem on Ubuntu 9.04 or 9.10 (using same hardware), so I was hoping somebody here might have an idea why this would have changed. I appreciate it if anyone can give some advice. I get this error using both jogl1.1.1 and jogl2.0-beta10, and I'm using Sun JDK 1.6 update 20. If there's any other info I can provide that would help, please let me know. 

Thanks

---

