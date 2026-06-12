---
title: "World Wind"
date: 2011-06-30
forum: General Help
---

### Post by cacs on 2011-06-30
Hi. I downloaded latest world wind worldwind-0.6.875.15822.zip) and run it with the command:
./run-demo.bash gov.nasa.worldwind.examples.ApplicationTemplate
It runs for a while (few seconds) and than: ./run-demo.bash: line 6:  3829 Aborted
any idea?
tya

---

### Post by sam_delta on 2011-06-30
Have you tried installing worldwind through the repositories? (either using ubuntu software center or apt-get?)

samd

---

### Post by cacs on 2011-06-30
> **sam_delta said:**
> Have you tried installing worldwind through the repositories? (either using ubuntu software center or apt-get?)

samd

Thank you samd!
Installed with the apt-get command after your post and it runs but still encounters the following error:

# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00263416, pid=4821, tid=2084678512
#
# JRE version: 6.0_22-b22
# Java VM: OpenJDK Server VM (20.0-b11 mixed mode linux-x86 )
# Derivative: IcedTea6 1.10.2
# Distribution: Ubuntu 11.04, package 6b22-1.10.2-0ubuntu1~11.04.1
# Problematic frame:
# C  [+0x416]  __kernel_vsyscall+0x2

That I don't know how to fix. :(

---

### Post by ajgreeny on 2011-06-30
TRy removing open-jdk and the icedtea plugin and installing sun-java packages in their place.  There are often problems with the open source java apps for some uses.

---

### Post by cacs on 2011-07-02
> **ajgreeny said:**
> TRy removing open-jdk and the icedtea plugin and installing sun-java packages in their place.  There are often problems with the open source java apps for some uses.

Hi! Ty. I tried removed  open-jdk and icedtea and installed sun-java and the worldwind simply doesn't run!

---

