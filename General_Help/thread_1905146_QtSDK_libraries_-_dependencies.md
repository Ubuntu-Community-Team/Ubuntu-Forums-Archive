---
title: "QtSDK libraries - dependencies"
date: 2012-01-06
forum: General Help
---

### Post by emirsokic on 2012-01-06
Hello,

I'm using Ubuntu 9.04, and trying to install a v4l2ucp package from a .deb. It says that "Error: Dependency is not satisfiable: libqtcore4 (>= 4:4.6.1)". libqtcore4 is installed on my system (I can see it in synaptic, version 4.5.1). 
Also QtSDK is installed on my system (the latest version), downloaded from "qt.nokia.com/downloads/", through an internet installer, and it has the latest libraries. QtSDK is installed in my home folder. This install is not visible in synaptic.

Is it possible to create some symbolic links or something, to resolve these dependencies?


I know, I should update my kernel and everything, but unfortunately I have so many things running and working on my computer, that I would lose 3 days to make it functional again. (That is the advantage of linux, it rarely crashes:-), so while it works I don't touch it).

Thanks

---

### Post by ajgreeny on 2012-01-06
Your library package version is not up to date hence the error message, and Ubuntu 9.04 is no longer supported, so I think you are going to find it very difficult to get the v4l2ucp package working.

It may be possible, as you suggest, to make links from the appropriate files now in your /home folder, to the same place in your filesystem as the old, current versions of the libqtcore4 files, but bear in mind that this could easily break other packages that depend on the current older library version.

All things considered, if this v4l2ucp package is so important to you, I suggest the distro upgrade to perhaps the 10.04 version of Ubuntu would be the best answer.

---

### Post by emirsokic on 2012-01-10
Thanks... I updated after all.

---

