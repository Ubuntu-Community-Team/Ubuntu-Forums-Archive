---
title: "dpkg - strange state after power loss - how to fix?"
date: 2011-10-25
forum: General Help
---

### Post by froff on 2011-10-25
hello
Recently I started process of installing about 1GB of packages using synaptic.
Unfortunatelly power loss occurs during this process.
It seems that it downloaded all packages from repo but almost all are not installed. synaptic gives errors when I try to install again packages, that are reported as not installed.
How to fix package structure and install everything again?

best regards

---

### Post by cryptotheslow on 2011-10-25
What exact errors does Synaptic give you?

If you cannot capture the errors easily from Synaptic - close it entirely. Then open a Terminal window and enter these commands:

```
sudo apt-get update
```

If that gives no errors do:

```
sudo apt-get upgrade
```

You should get the same errors here that Synaptic gives - so copy all the output and post it back here between "CODE" tags by using the # button on the toolbar.

---

