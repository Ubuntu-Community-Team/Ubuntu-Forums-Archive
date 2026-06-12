---
title: "Preventing an app from updating with apt-get"
date: 2011-10-02
forum: General Help
---

### Post by shukalo83 on 2011-10-02
Hello.

I need some help with compiling new software. If I wanted new version of e.g. Deluge bittorrent client and want to compile it, (version 1.3.0 that I'm using has bugs). So let's say I compiled and installed with sudo make install, how can I prevent that new version of being overrun by apt-get. I know that I can uninstall deluge with apt-get completely with apt-get remove but I don't want to do that.

Thank you all.

---

### Post by dave01945 on 2011-10-02
if you compile and install a program using *sudo make install* it will not be managed by apt-get

if it is installed with apt-get you can hold a package version so that it doesn't update during upgrades not sure how you can do that with apt-get but you can do it with aptitude or synaptic

---

### Post by ajgreeny on 2011-10-02
You can pin your current package or packages as follows:-
To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version (number currently installed)
Pin-Priority: 1001
```

---

### Post by SeijiSensei on 2011-10-02
> **dave01945 said:**
> if you compile and install a program using *sudo make install* it will not be managed by apt-get

Indeed, you should use "sudo apt-get remove deluge" so that later updates won't try to reinstall the packaged version.  If everything installed by "make install" appears under /usr/local, as it should, I'd use "purge" rather than "remove" when deleting the packaged version of Deluge.

---

### Post by shukalo83 on 2011-10-03
Thank You all. Pin option is what I have been looking for. Nevertheless, other comments were interesting too.

---

