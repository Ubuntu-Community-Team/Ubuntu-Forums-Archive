---
title: "Synaptic says some packages are held back. Is this bad?"
date: 2009-11-23
forum: General Help
---

### Post by jazzvibes on 2009-11-23
Hi 

Synaptic says I have a number of packages that will be held back and not upgraded.

Is this a problem? What is it caused by? Can I find out which programs are the culprits and fix it?

Cheers.

FYI the packages include some avahi, some gstreamer, transmission, and linux-headers and a few others....

---

### Post by Native Dialect on 2009-11-23
You are limiting the repositories that the synaptic pack manager has access to. You can change this however.

synaptic package manager > settings > repositories 

From there, you can choose which repositories you use.

---

### Post by bodhi.zazen on 2009-11-23
Try updating from the command line :

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by sgosnell on 2009-11-23
It depends on what you're trying to do.  If you're just installing new packages, it's good.  It means those packages aren't affected, and won't be removed.  You only need to start worrying when many packages are going to be removed.  If that happens, you need to cancel and think about what is going on before you commit to anything.

---

