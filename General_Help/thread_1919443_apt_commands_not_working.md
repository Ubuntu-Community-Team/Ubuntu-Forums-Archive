---
title: "apt commands not working"
date: 2012-02-02
forum: General Help
---

### Post by romain.astie on 2012-02-02
Hi all,

whenever I try to install a new package using apt-get, I get an error message that says that it could not locate the package I'm trying to install. any ideas as to why this is? Also, it seems that no apt command, like apt-cache search, works...
I'm running lubuntu 11.10, can you help me?

---

### Post by oldos2er on 2012-02-02
Can you post the output from ```
sudo apt-get update && sudo apt-get upgrade
``` ?

---

### Post by romain.astie on 2012-02-02
It look as if apt-get upgrade and apt-get update are the only apt commands that work so far. My internet is slow and buggy, so my computer (336MHz CPU, by the way) may need to work through the night....

---

### Post by drmrgd on 2012-02-03
> **romain.astie said:**
> It look as if apt-get upgrade and apt-get update are the only apt commands that work so far. My internet is slow and buggy, so my computer (336MHz CPU, by the way) may need to work through the night....

This might be overly basic, but are you sure you've typed the package name correctly?  The package names are case-sensitive and need to be typed exactly as they are listed in the repository.  You might have the name correct already, but it's a quick and simple thing to check.  

Another simple thing to check is whether or not you can find and install the package graphically.  Can you find the package and install it from Synaptic Package Manager?

---

### Post by romain.astie on 2012-02-03
The upgrade and update commands suggested fixed the problem... Thanks

---

### Post by oldos2er on 2012-02-03
If your problem is fixed, could you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

