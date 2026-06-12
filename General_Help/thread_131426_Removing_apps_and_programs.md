---
title: "Removing apps and programs"
date: 2006-02-16
forum: General Help
---

### Post by floyd27 on 2006-02-16
Hey..
Im posting to ask how to remove things that I installled either through apt-get or synaptic..

I ask because when I choose to remove or uninstall it through apt-get or synaptic, it usually says its going to remove the ubuntu-desktop as well. This causes me to abort the uninstall..

Is there a command that will allow me to only remove the specific app in question?
thanx again

---

### Post by alfonz on 2006-02-16
well if it tells you that it will remove the ubuntu-desktop then it is probably dependent on them, however I have never come across that before.

if you want to uninstall something open terminal and type:

```
sudo apt-get remove <application name>
```

or 

```
sudo apt-get remove --purge <application name>
```

becarefull with this one, it also might get rid of some dependencies that other programs need.

---

