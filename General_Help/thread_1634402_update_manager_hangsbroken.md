---
title: "update manager hangs/broken"
date: 2010-11-30
forum: General Help
---

### Post by jworr on 2010-11-30
On ubuntu 10.10 when I run the update manager and click the "install updates" button the program will pause for a moment then do nothing.  When I run update manager from a terminal there is no output, the updates are simply not installed.  Does anyone know a solution for this?

---

### Post by plucky on 2010-11-30
> **jworr said:**
> On ubuntu 10.10 when I run the update manager and click the "install updates" button the program will pause for a moment then do nothing.  When I run update manager from a terminal there is no output, the updates are simply not installed.  Does anyone know a solution for this?

What happens when you run from a terminal ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jworr on 2010-11-30
Those commands execute normally, and I'm able to update my machine via synaptic too

---

### Post by madjr on 2010-11-30
it may be a bug in update manager after upgrading from a previous release. some people encounter it.

---

