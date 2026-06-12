---
title: "How do I get a list of packages that I installed deliberately?"
date: 2011-02-23
forum: General Help
---

### Post by sixcorners on 2011-02-23
In MacPorts, the ports I would be looking for are the requested ports. They have a system so that when you install a port, that port is marked as requested. Also if you want to keep a port that was installed as a dependency, you can set it to be requested manually. Does the Debian system have the same functionality? It seems that there are some utilities that get that done..

---

### Post by An Sanct on 2011-02-23
[Synaptic]("http://www.nongnu.org/synaptic/") has got a filter for that.

---

### Post by Habitual on 2011-02-23
```
dpkg --get-selections | grep install > installed.txt 
```

---

### Post by sixcorners on 2011-02-24
> **An Sanct said:**
> [Synaptic]("http://www.nongnu.org/synaptic/") has got a filter for that.
I had seen that and thought that it was actually filtering out packages that were dependencies. Now that I compared Automatic Install to Manual Installed I see that they are entirely different lists..

> **Habitual said:**
> ```
dpkg --get-selections | grep install > installed.txt 
```

I guess I just didn't understand that all of those library packages that I thought were dependencies were actually installed as packages that were "requested" or "selected." I thought they would all be installed through some ubuntu metapackage like ubuntu-desktop. Is it possible to install ubuntu as a small handful of packages that depend on everything else that needs to be installed?

---

