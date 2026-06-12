---
title: "synaptic package manager problem"
date: 2009-07-27
forum: General Help
---

### Post by j.e.schroder on 2009-07-27
every time i go to open the synaptic package manager i get the message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

this also happens when i try to install any new package using any package manager. i have no clue whats going on. can someone nudge me in the right direction?

---

### Post by blazemore on 2009-07-27
The solution is usually simple.

Open a Terminal
Applications -> Accessories -> Terminal

Type the following:
```
sudo dpkg --configure -a
```
Press Enter

Type your password (There will be no visual feedback, this is expected)
Press Enter.

Hopefully that will solve the problem. If not, please post the results of running the above command here, and I will try and help you further.

---

### Post by j.e.schroder on 2009-07-30
found the problem, i left some fodder in sources.list. however now an error message comes up when i try to install anything:
"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is running. Please close that application first."

But i only use the Synaptic, the  one that came with Ubuntu.

---

