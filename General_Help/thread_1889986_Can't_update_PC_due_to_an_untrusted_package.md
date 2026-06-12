---
title: "Can't update PC due to an untrusted package"
date: 2011-12-02
forum: General Help
---

### Post by YourSurrogateGod on 2011-12-02
I tried updating my machine with Synaptic and this is the error that I got.  Thoughts?  I trust it enough to install, any way I can force its install?

> Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

```
apt apt-transport-https apt-utils update-manager update-manager-core update-notifier update-notifier-common
```

---

### Post by YourSurrogateGod on 2011-12-02
Meh:
```
sudo apt-get upgrade
```

Not the best solution, but did it.

---

