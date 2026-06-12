---
title: "Java on 64bit"
date: 2009-09-24
forum: General Help
---

### Post by mikeym on 2009-09-24
Hi,

I'm running 64 bit ubuntu and I seem to have some form of java installed but I can't use java through my browser (firefox) and I get a really ugly theme when I try and run an application.

There are a terribly confusing set of Java implementations available and I don't know which ones work on 64bit systems. Could someone please tell me what I need?

My current version is *java -version*

```
java version "1.5.0_19"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_19-b02)
Java HotSpot(TM) 64-Bit Server VM (build 1.5.0_19-b02, mixed mode)

```

---

### Post by mikeym on 2009-09-24
Sorry to bump this but I can't see that Java on a 64bit system is an obscure question and I have read the community documentation and the Official Server documentation and am none the wiser.

---

### Post by Rob_H on 2009-09-24
The Java runtime environment and the Java browser plugin are two different things. Make sure you have installed the **sun-java6-plugin** package. Then start Firefox, and type "about: plugins" (without the space) into the address bar and make sure the Java plugin is listed there.

---

### Post by mikeym on 2009-09-24
Thanks.

That seemed to work. I thought there was some issues with sun-java and 64 bit. There doesn't appear to be so now. I installed sun-java6-plugin and sun-java6-bin and sun-java6-rte

---

### Post by Rob_H on 2009-09-24
> **mikeym said:**
> I thought there was some issues with sun-java and 64 bit.

The Sun Java VM has supported 64-bit Linux for some time, but there was no 64-bit browser plugin until recently. Maybe that's the issue you're thinking of.

---

