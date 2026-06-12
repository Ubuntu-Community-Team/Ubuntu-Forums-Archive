---
title: "NetBeans trouble after update"
date: 2009-11-12
forum: General Help
---

### Post by ajmurmann on 2009-11-12
I updated a few days ago to Karmic under 64 Bit, I had a few problems that probably are unrelated (see below). When I started up NetBeans (which now is 6.7.1) after the update some plugin modules couldn't be loaded anymore. It didn't give any reasons for that. I tried to activate these modules but it just said that it can't do it; again no reason given. Reinstall of NetBeans didn't change anything. So I completely removed NetBeans via Synaptic and installed it again. Now NetBeans doesn't startup anymore at all. I get the following error on the terminal which seems to be Java related:

```
Unrecognized option: -client
Could not create the Java virtual machine.
```I am using Sun Java and all other Java apps seem to be running fine. 


I had the following problems during the update to Karmic, which are probably unrelated: I had a power outage during the update after which the system stopped during startup waiting for something I can't remember. However I booted from the Ubuntu CD to recovery console and finished teh upgrade after which everything worked fine, besides the NetBeans issue.



Thank you very much for any help!

---

### Post by ajmurmann on 2009-11-13
It tuned out that the JDK Home in /usr/share/netbeans/6.7.1/etc/netbeans.conf was set to OpenJDK, which is not my system default. I changed the JDK home to "/usr/lib/jvm/java-6-sun" and everything works fine now.

---

