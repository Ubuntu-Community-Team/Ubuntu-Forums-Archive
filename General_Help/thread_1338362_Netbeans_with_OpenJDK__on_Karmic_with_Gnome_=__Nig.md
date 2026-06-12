---
title: "Netbeans with OpenJDK  on Karmic with Gnome =  Nightmare"
date: 2009-11-26
forum: General Help
---

### Post by Zeratul021 on 2009-11-26
Have anyone else ran into this issue?

NetBeans is spilling huge amount of errors and crashes randomly on some gui actions (right click) or keeps looping over one exception.

When ran from terminal, some info remains there related to GUI with --sync option.

It was working perfectly to 9.04 with GNOME & KDE, it is working perfectly on 9.10 with KDE but not in 9.10 with GNOME.

Issue seems to be solved with installing of java-6-sun and running with this realease.

Again, anyone else had a similar issue with openjdk (what's wrong with it??) on ubuntu 9.10?

Regards,

Marek

---

### Post by pi4r0n on 2009-11-26
Looks OK for me (no errors). Might want to re-check you settings.

---

### Post by emachnic on 2009-11-26
Open JDK tends to be a bit buggy. I always install sun-java6 and haven't had any abnormal problems with either Netbeans or Eclipse. I think it actually has something to do with a conflict between GTK and Open JDK and that's why it doesn't happen on KDE

---

### Post by lpanebr on 2009-11-26
ok, sorry for my ignorance but how to remove the JDK and install sun-java6?

thanks

---

### Post by emachnic on 2009-11-26
Use synaptic and make sure to completely remove all instances of open jdk. Then search for sun-java6 and install everything except sun-java6-doc (that tends to throw errors).

---

### Post by Zeratul021 on 2009-11-26
> Open JDK tends to be a bit buggy. I always install sun-java6 and haven't had any abnormal problems with either Netbeans or Eclipse. I think it actually has something to do with a conflict between GTK and Open JDK and that's why it doesn't happen on KDE

Agreed, but as I said, worked in versions before so maybe would need som research/debug to report a bug. Settings... too general in OS and its fresh install.

> ok, sorry for my ignorance but how to remove the JDK and install sun-java6?

thanks

It's not like in M$ Win. You don't have to remove it, just install sun's java and then change your shell variable JAVA_HOME. Or edit ~/netbeans-XX/etc/netbeans.conf and change netbeans_jdkhome to sun's java home. 


HTH

Marek

---

### Post by hamed.obaidy on 2009-12-24
You can install sun-java6 and use update-java-alternatives as root and change default jdk to sun-java6

---

