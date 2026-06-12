---
title: "Need some information on openjdk &amp; netbeans"
date: 2010-05-03
forum: General Help
---

### Post by ganeshmallyap on 2010-05-03
Hi all,

I have installed Lucid AMD64 on my desktop yesterday successfully.  Now I wanted to know whether we can install NetBeans IDE with JDK.  By default it will look for Sun Java.  When I installed Ubuntu-Restricted-drivers, it had installed OpenJDK.  

I am also curious to know can we have both OpenJDK & SunJava installed on the same machine and running simultaneously without any conflicts/issues?

Thanks in advance.

Regards
Ganesh

---

### Post by CoreyB. on 2010-05-04
> **ganeshmallyap said:**
> Hi all,

I have installed Lucid AMD64 on my desktop yesterday successfully.  Now I wanted to know whether we can install NetBeans IDE with JDK.  By default it will look for Sun Java.  When I installed Ubuntu-Restricted-drivers, it had installed OpenJDK.  

I am also curious to know can we have both OpenJDK & SunJava installed on the same machine and running simultaneously without any conflicts/issues?

Thanks in advance.

Regards
Ganesh

Netbeans will look for the default-jdk package, which in lucid points to openjdk-6-jdk.  You can have both Sun java and OpenJDK installed simultaneously without conflicts.

---

### Post by ganeshmallyap on 2010-05-04
Thank you so much Corey. Let me try doing this. Thanks again.

Ganesh

---

