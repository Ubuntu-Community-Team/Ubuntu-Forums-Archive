---
title: "How do you stop an upgrade from over writing a custom source compilation?"
date: 2010-12-13
forum: General Help
---

### Post by vfclists on 2010-12-13
I created a customized version of a package, and when I did an upgrade later the source build got overwritten.

How can I configure the package system to stop that from happening even if the main repositories have newer versions?

---

### Post by QLee on 2010-12-13
[QUOTE=vfclists]I created a customized version of a package, and when I did an upgrade later the source build got overwritten.

How can I configure the package system to stop that from happening even if the main repositories have newer versions?[/QUOTE]

Since you are an advanced user, I'm just going to give you the topic. What you want to investigate is "apt pinning", you set the priority of your package version in the "preferences" to be higher than the version of the upgrades. This is like using a "hold" in Synaptic.

---

### Post by ajgreeny on 2010-12-13
Have you found it yet?  If not:-

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name                
Pin: version (number from repos)    
Pin-Priority: 1001
```
I note the priority number in this is different to that which I see on some search findings; I don't know how important that is, I'm afraid, or if it more to do with user and root uid.

Nor do I know quite how you will manage to add a version number to your compiled package; I'll have to let you sort that out yourself.

---

### Post by QLee on 2010-12-14
> I note the priority number in this is different to that which I see on  some search findings; I don't know how important that is, I'm afraid, or  if it more to do with user and root uid.

Nothing to do with user or root ids.

In this specific case, since the package is available locally, the OP might use 
 Pin: origin ""
instead of version number set at compile time. And any number above 990 would likely accomplish the task, unless a target release is specified, which it probably isn't so, any number above 500 would likely work.

However, the OP has probably already figured this out since there weren't any follow up questions.

---

### Post by vfclists on 2010-12-31
I don't regard myself as an advanced user, but it is nice to be described as such:). I am sure I have done something like that before and forgotten about it.

Thanks for the reminder.

> **QLee said:**
> Since you are an advanced user, I'm just going to give you the topic. What you want to investigate is "apt pinning", you set the priority of your package version in the "preferences" to be higher than the version of the upgrades. This is like using a "hold" in Synaptic.

---

### Post by dcstar on 2010-12-31
> **QLee said:**
> Since you are an advanced user, I'm just going to give you the topic. What you want to investigate is "apt pinning", you set the priority of your package version in the "preferences" to be higher than the version of the upgrades. This is like using a "hold" in Synaptic.

Be aware that Pinning packages in Synaptic is ignored in Ubuntu Version Upgrades (known bug), but I don't know if that also happens to APT Pinning (which uses a different database than Synaptic).

This applies to Upgrades, not Updates.

---

### Post by Yellow Pasque on 2011-01-01
I prefer to use checkinstall to create a .deb for the source build and give it a higher version than what's in the repo.

---

