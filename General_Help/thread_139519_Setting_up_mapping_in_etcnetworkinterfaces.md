---
title: "Setting up mapping in /etc/network/interfaces"
date: 2006-03-04
forum: General Help
---

### Post by bensexson on 2006-03-04
If have been trying to control my wireless during bootup with scripts.  I have it working but now I would like to set it up using mapping.  Unfortunately I have been unable to find a good guide for setting up mapping.  Does anyone know a good doc or HOWTO for mapping?

---

### Post by bensexson on 2006-03-06
bump

---

### Post by silhouette on 2006-03-06
I'm not sure what you mean by mapping (not quite familiar with Linux terminology, sorry) but have you tried
```
$ man interfaces
```
yet?

---

### Post by bensexson on 2006-03-08
Yes, it directs you to the examples installed instead of actually expaining the rules for mapping.  I have looked at the examples but still have questions about how it actually works.

---

### Post by bensexson on 2006-03-14
bump

---

### Post by Ramses de Norre on 2006-03-14
What does mapping do? I have this lines in my /etc/network/interfaces: ```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

```
Though I don't use eth0.

---

### Post by bensexson on 2006-03-14
I don't use Breezy yet (gcc compatibility issues) so I have only recently seen this.  Mapping allows virtual interfaces to be setup in the interfaces file to allow different settings for a physical interface. A script is called (in your case hotplug) to automatically determine which virtual interface to use.  The file you have is the default in Breezy and allows hotplug to bring up eth0.

---

