---
title: "install eclipse 3.5 galileo in jaunty"
date: 2009-11-12
forum: General Help
---

### Post by pythonscript on 2009-11-12
How do I install the newest version of eclipse on jaunty? The version in jaunty's default repos is 3.2, and I'd like to install 3.5. I added the eclipse ppa to /etc/apt/sources.list and verified the key by adding:

```
deb [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) jaunty main 
deb-src [http://ppa.launchpad.net/eclipse-team/ppa/ubuntu](http://ppa.launchpad.net/eclipse-team/ppa/ubuntu) jaunty main 
```

and running:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com DCC7AFE0

```

but when I upgrade my system... the newest version isn't available. I'd like to officially install it, not just run it from the tar.gz archive every time. Any ideas? Thanks!

---

### Post by pythonscript on 2009-12-07
Does anyone have any ideas? It's a pain having to move to the windows side of my machine just to work with eclipse. Thanks!

---

### Post by xannen on 2011-06-16
I am experiencing a similar problem.

It is a common problem, with linux and software update, particular for distribution that does not have direct relation with the software.

Another odd problem, and this may simply be an Eclipse problem, when using Eclipse built-in update function, there seem to be version conflicts and unresolved dependency.  Eclipse does not try to uninstall outdated version, and put the new one in.  For the second problem, Eclipse should try to locate or download the dependency for installation.

---

