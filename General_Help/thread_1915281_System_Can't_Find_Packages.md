---
title: "System Can't Find Packages"
date: 2012-01-25
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2012-01-25
As part of troubleshooting the lack of sound on my laptop using the steps at

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

, I typed

```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```at the cl and the response was

```

E: Unable to locate package linux-restricted-modules-3.0.0-15-generic
E: Couldn't find any package by regex 'linux-restricted-modules-3.0.0-15-generic'

```I've tried ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```. Restricted is checked in synaptic.

---

