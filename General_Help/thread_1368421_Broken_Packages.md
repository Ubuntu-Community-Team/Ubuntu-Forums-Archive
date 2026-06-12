---
title: "Broken Packages"
date: 2009-12-30
forum: General Help
---

### Post by Scott O'Nanski on 2009-12-30
Can't install a deb. 9.10 bounces back a message that says I have broken packages.

Synaptic is blank for broken packages.

How do I find which packages are broken, and how do I fix them?

Googled. Nothing.

---

### Post by taurus on 2009-12-30
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Make sure you close synaptic first before you run those two commands from a terminal.

---

