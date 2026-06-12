---
title: "I need help"
date: 2011-09-23
forum: General Help
---

### Post by Yazn on 2011-09-23
I'm beginner user of Ubuntu and need help .. I tried to install gparted  and it was failed I wrote this code 
sudo apt-get install gparted 

and the result is 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages

---

### Post by dave01945 on 2011-09-23
try to run this first

```
sudo apt-get update
```

then try to install again

```
sudo apt-get install gparted
```

and let us know what happened

---

### Post by MAC59 on 2011-09-23
> **dave01945 said:**
> try to run this first
 
```
sudo apt-get update
```
 
then try to install again
 
```
sudo apt-get install gparted
```
 
and let us know what happened
 
 
Once the above is done, Use Synaptic Package manager to install the package it will retreive all the packages and install them. Once that is done you should be golden.

---

### Post by seawolf167 on 2011-09-23
> **MAC59 said:**
> Once the above is done, Use Synaptic Package manager to install the package it will retreive all the packages and install them. Once that is done you should be golden.

The second command that was posted installs the package and attempts to satisfy all dependencies, so opening the Synaptic Package Manager is necessary. There are four ways to install packages:

[LIST]
[*]Ubuntu Software Center
[*]Synaptic Package Manager
[*]apt-get
[*]aptitude
[/LIST]
all of which are essentially the same (i.e. GUI vs. front-end, etc.). *Yes *there are differences (like between apt-get and aptitude), but none that you'll have to worry about at this stage of the game.

---

