---
title: "How To Upgrade a .deb File"
date: 2012-05-23
forum: General Help
---

### Post by CarlosinFL on 2012-05-23
So I've installed an application on 12.04 which just required me to download / install the file with one simple command:

```
sudo dpkg -i <some_packagae>.deb
```

My question is now there's a new version of the software available. Does Ubuntu / Debian prefer that I remove the package 1st and then re-run the same command above but with the newer version or is it recommended / safe to roll the installation over the existing one?

---

### Post by zvacet on 2012-05-23
Remove and rerun.

---

### Post by CarlosinFL on 2012-05-24
Lets say I installed the VMware package a year ago and I deleted the original .deb file used to install on my system...how can I know what the file name is that I have to remove using the 'dpkg -r' command?

---

### Post by matt_symes on 2012-05-24
Hi

To get clues try something like

```
dpkg -S vmware
```

```
dpkg -l vmware
```

Small L after dpkg.

```
dpkg -l | grep vmware
```

```
dpkg -l | grep virtual
```

Searches like that can help.

Kind regards

---

### Post by odiseo77 on 2012-05-24
If you know some part of the package name, you can execute:

```
dpkg -l | grep -i vmware
```

It will tell you which packages containing the pattern "vmware" are installed on the system.

You can also execute:

```
sudo dpkg -r vm<tab>
```

And let bash complete the name or suggest a name from the installed packages matching the pattern.

---

### Post by CarlosinFL on 2012-05-24
Thanks for the clues and help using dpkg! :guitar:

---

