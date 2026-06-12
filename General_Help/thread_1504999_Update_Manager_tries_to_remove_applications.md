---
title: "Update Manager tries to remove applications"
date: 2010-06-08
forum: General Help
---

### Post by SanderSchobers on 2010-06-08
I was wondering why some programs are removed when doing a (partial) upgrade. For instance the Nvidia drivers, the network manager and some other server components are removed.

This is very annoying since you're receiving updates on a regular basis.

(screenshot of the update manager announcing the programs it's going to remove)

[ATTACH]159774[/ATTACH]

---

### Post by Frogs Hair on 2010-06-08
If you are upgrading, packages will be removed and replaced by packages needed for the upgrade that includes drivers . your current video driver may not be compatible with the upgrade , in that case you must install the the recommended driver after updates are completed.

---

### Post by LowSky on 2010-06-08
> **Frogs Hair said:**
> If you are upgrading, packages will be removed and replaced by packages needed for the upgrade that includes drivers . your current video driver may not be compatible with the upgrade , in that case you must install the the recommended driver after updates are completed.

Exactly what I would say.

---

### Post by philinux on 2010-06-08
double post oops

---

### Post by philinux on 2010-06-08
> **SanderSchobers said:**
> I was wondering why some programs are removed when doing a (partial) upgrade. For instance the Nvidia drivers, the network manager and some other server components are removed.

This is very annoying since you're receiving updates on a regular basis.

(screenshot of the update manager announcing the programs it's going to remove)

[ATTACH]159774[/ATTACH]

which version you running

---

### Post by Boondoklife on 2010-06-08
Be very careful with partial upgrades they can hose your system.

You may wish to review tis article:
[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

---

### Post by SanderSchobers on 2010-06-09
I'm running version 10.04, installed very recently upgraded once or twice. The curious thing, they are removed but not replaced. For example I already had to install/activate the *recommend* Nvidia driver twice.

And for example the network-manager is (I think) installed in from DVD but uninstalled with the first upgrade. Installed again but now it's trying to remove this handy tool again. I installed the NFS kernel server (as a long support package) and it's still trying to remove that.

It would be fine if I knew that these applications would be upgraded/reinstalled but it doesn't look like this.

---

