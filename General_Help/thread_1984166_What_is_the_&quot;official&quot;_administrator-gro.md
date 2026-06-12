---
title: "What is the &quot;official&quot; administrator-group as of 12.04 ?"
date: 2012-05-21
forum: General Help
---

### Post by bokopperud on 2012-05-21
For 12.04:  What is the official/recommended group to add users who should get root-privileges to?  Previously it's been the admin-group, but it's seems to have been retired...

Is this an Ubuntu-specific change, or something originating from Debian?

---

### Post by rai4shu2 on 2012-05-21
Actually, the group is (and has been) "admin" since at least 8.04.

see: [https://help.ubuntu.com/community/Sudoers#The_Default_Ubuntu_Sudoers_File](https://help.ubuntu.com/community/Sudoers#The_Default_Ubuntu_Sudoers_File)

In fact, I can't recall it ever being called "admin-group".

---

### Post by oldfred on 2012-05-21
There seems to have been some change:

ReleaseNotes:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

> Up until Ubuntu 11.10, administrator access using the sudo tool was  granted via the "admin" Unix group. In Ubuntu 12.04, administrator  access will be granted via the "sudo" group. This makes Ubuntu more  consistent with the upstream implementation and Debian. For  compatibility purposes, the "admin" group will continue to provide  sudo/administrator access in 12.04. 


---

### Post by mc4man on 2012-05-21
On a fresh install there will be no "admin" in /etc/groups, sudo is what's used now
master bug on
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842)

---

### Post by bokopperud on 2012-05-21
admin-group as in "a group named admin", not that the group was called "admin-group".  Sorry for my unclear English...

---

