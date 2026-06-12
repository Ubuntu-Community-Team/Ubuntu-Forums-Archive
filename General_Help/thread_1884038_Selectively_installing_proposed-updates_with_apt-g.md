---
title: "Selectively installing proposed-updates with apt-get"
date: 2011-11-20
forum: General Help
---

### Post by wonko on 2011-11-20
I'm trying to follow [this guide]("https://wiki.ubuntu.com/Testing/EnableProposed") to install the proposed version of libmsn0.3 without upgrading my whole system to proposed versions, but the guide suggests using aptitude while I want to use apt-get. I tried ```
sudo apt-get install libmsn0.3/oneiric-proposed
 and 
sudo apt-get install -t=oneiric-proposed libmsn0.3
``` but both says "libmsn0.3 is already the newest version". "apt-cache show" reports Version: 4.1-2ubuntu1, but I'm pretty sure the proposed-repo has version 4.1-2ubuntu1.1 (at least it says so [here]("http://packages.ubuntu.com/oneiric-updates/libmsn0.3")), which has the bugfix I'm interested in. 

How can I force apt-get to install version 1.1 like they do with aptitude in the guide I linked to?

---

