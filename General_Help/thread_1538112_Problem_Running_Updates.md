---
title: "Problem Running Updates"
date: 2010-07-24
forum: General Help
---

### Post by aaronfox03 on 2010-07-24
I recently started running Ubuntu. The Updates are piling up in the Update Manager, and for some reason I cannot get any of them to run. I click Install Updates, I get the "reading Package" box. Then nothing.... Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2010-07-24
Open a terminal and enter :

```
sudo apt-get update && sudo apt-get upgrade
```

Post any errors you receive.

---

### Post by linux18 on 2010-07-24
this might be a good place for my " fix 90% of all synaptic errors " shell script:

```
  #!/bin/bash
####   Fix all synaptic errors   ###

sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
sudo apt-get clean || echo "ERROR 3"
apt-get autoclean || echo "ERROR 4"
sudo apt-get autoremove || echo "ERROR 5"
sudo apt-get update || echo "ERROR 6"
sudo apt-get upgrade || echo "ERROR 7"
echo "100% DONE" 
```

---

### Post by aaronfox03 on 2010-07-24
I ran the code and it downloaded the updates. Buuuut, now my desktop is messed up. I also keep getting a Crash Report, but when I click on it, it wont open at all. Now I cant get any administrative task to open? I didnt try running your script though...

---

