---
title: "kubuntu limewire and google-chrome wont start. Help needed"
date: 2010-03-08
forum: General Help
---

### Post by eser_87 on 2010-03-08
a   
Hi everyone,

I am a Kubuntu Karmic Koala user. Having some  trouble using limewire and google chrome. Well the problem about  Limewire is, it wont work. I cant start it. When i start it i get an  error like below 

```

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_15]
Configuring environment...
Loading LimeWire:
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0xb770d47e, pid=13920, tid=2640698224
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Server VM (14.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [ld-linux.so.2+0x1647e]
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid13920.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
./runLime.sh: line 124: 13920 Aborted                 
${JAVA_PROGRAM_DIR}java -Xms64m -Xmx256m -ea:com.limegroup... -ea:org.limewire... 
-Djava.net.preferIPV6Addresses=false -Djava.net.preferIPv4Stack=true 
-Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog 
-Djava.library.path=. 
-Djna.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.6+)
The version of Java in your PATH is:
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)




```Apparently  it something about Java HotSpot server. I have sun java jdk and jre 1.6  installed. No idea how to solve the problem. Anyone that can help ?



And  the problem about Google-chrome is when i start it i get the error  below and it also doesn't start.



```
[14423:14423:13899317349:FATAL:/usr/local/google/b/slave/chrome-official-linux/build/src/chrome/browser/browser_main.cc(755)] Check failed: profile. Cannot get default profile.
Trace/breakpoint trap

```

---

### Post by rogue_0111 on 2010-03-08
for limewire try (BTW: limewire sux):

[http://www.gnutellaforums.com/general-linux-support/39850-how-install-limewire-ubuntu-debian.html](http://www.gnutellaforums.com/general-linux-support/39850-how-install-limewire-ubuntu-debian.html)

or

[https://help.ubuntu.com/community/LimeWire](https://help.ubuntu.com/community/LimeWire)


hope this helps

---

### Post by eser_87 on 2010-03-10
Thanks a lot. The firs link solved the problem :) 


And why do u think limewire sucks ?  Any better alternative you can suggest ?

---

### Post by rogue_0111 on 2010-03-10
It just does. Do some more reading:)

Glad I could help.

---

### Post by eser_87 on 2010-03-11
Thanks :) That really helped. Google-chrome problem still exist though :(

And for limewire. It is sufficient for me :)

---

