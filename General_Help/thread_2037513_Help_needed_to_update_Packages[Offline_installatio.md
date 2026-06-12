---
title: "Help needed to update Packages[Offline installation]"
date: 2012-08-04
forum: General Help
---

### Post by Yuva Raj on 2012-08-04
Hi,

Whenever i run this command to install package,

Sudo apt-get install packagename.deb

i get this error,,

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

Please help me :)

---

### Post by oldos2er on 2012-08-04
Do you have the universe repository enabled? Which version of Ubuntu are you running?

Try ```
sudo apt-get update && sudo apt-get install synaptic
```
This assumes you have a working internet connection. If you don't, try [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

---

### Post by Yuva Raj on 2012-08-05
> **oldos2er said:**
> Do you have the universe repository enabled? Which version of Ubuntu are you running?

Try ```
sudo apt-get update && sudo apt-get install synaptic
```
This assumes you have a working internet connection. If you don't, try [https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

First & Foremost i need to install my synaptic package manager.

Please ! Help me to install in Offline mode.
I have even Package ..But it has dependency.

How to resolve it?

---

### Post by Yuva Raj on 2012-08-05
Bump!

---

### Post by Shadius on 2012-08-05
> **Yuva Raj said:**
> Hi,

Whenever i run this command to install package,

Sudo apt-get install packagename.deb

i get this error,,

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate

Please help me :)

This might help you. [Offline Synaptic Installation/Repository Updates]("http://ubuntuforums.org/showthread.php?t=1901446")

---

### Post by oldos2er on 2012-08-05
> **Yuva Raj said:**
> Please ! Help me to install in Offline mode.
I have even Package ..But it has dependency.

How to resolve it?

The link I gave you tells you how.

---

