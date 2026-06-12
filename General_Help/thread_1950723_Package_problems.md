---
title: "Package problems"
date: 2012-04-01
forum: General Help
---

### Post by jmacx81 on 2012-04-01
I have this problem that developed while I was in Afghanistan. Now I'm home and can't figure out how to fix it. Could someone please help with this... I try to run apt-get install and this is the message I get in the terminal.

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```

Then if I try to open the update manager, I get this warning

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'"

---

### Post by codemaniac on 2012-04-01
Hello jmacx81
Try the below in your terminal .

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by kc1di on 2012-04-01
try this command in a terminal:
```
sudo rm /var/lib/apt/lists/* -vf
```
then type ```
sudo apt-get update 
```
see what happens.

guess codemaniac and I were typing at same time :)

---

### Post by jmacx81 on 2012-04-01
Thanks, All seems to be working pretty good now, just doing an update.

---

### Post by codemaniac on 2012-04-01
Great to hear that .
yeah kc1di .. :) anyways have some popcorn :popcorn:

---

