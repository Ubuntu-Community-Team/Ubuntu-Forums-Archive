---
title: "Sun's Java in Jaunty barely working (1.6 u14)"
date: 2009-07-21
forum: General Help
---

### Post by sola on 2009-07-21
Guys,

I had serious, multiple issues with Sun's Java6 in Jaunty and most of them I believe can be linked to the shipped Java version of Jaunty.

Jaunty ships OpenJDK by default but for a number of reasons, most of the Java using people quickly replaces that with Sun's Java.

Jaunty ships with the version 1.6 update 14 of the Sun Java JDK/JRE/Plugin, it can be easily installed from Synaptic.

The issues I had:
- I experienced serious performance degradation in the Netbeans IDE (6.5).
- The Java 6 Plugin Control Panel is screwed, you cannot access the Cache Viewer's button
 - Webstart applications don't seem to update when a JAR changes on the server (this practically makes them impossible to update)
- TimeSlotTracker and Netbeans seems to somehow lock each other (they are started in separate Java VMs). TimeSlotTracker usually got frozen.

It was possible to downgrade Java back tu 1.6 Update 13 which seems to work correctly, as expected. I used this as a guide for downgrading Java: [http://www.skorks.com/2009/07/downgrading-a-ubuntu-package/](http://www.skorks.com/2009/07/downgrading-a-ubuntu-package/)

Some of these problems exist even on Windows version of 1.6 u14 (the Webstart JAR update problem for example).

---

### Post by sola on 2009-07-24
A nice addition:

u14 doesn't have the traditional /usr/lib/jvm/java-6-sun symlink to the real jdk folder so all of the previously generated WebStart icons stopped working.

---

