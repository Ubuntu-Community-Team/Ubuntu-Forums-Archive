---
title: "bzr explorer fails to start in karmic"
date: 2009-12-16
forum: General Help
---

### Post by Yumi on 2009-12-16
I added the bazaar ppa repositories. 
Through synaptic-package-manager installed "bzr explorer" and its dependencies. 
It added a entry to "applications -> programming"

Application fails to lauch from menu as from terminal. Terminal error is > michael@michael-desktop:~$ bzr explorer
bzr: ERROR: [Errno 2] No such file or directory: '/home/michael/.bazaar/explorer

What can I do?

Michael

---

### Post by andrewsomething on 2009-12-18
This was a known bug that should be fixed in the new release:

[https://bugs.edge.launchpad.net/bzr-explorer/+bug/474812](https://bugs.edge.launchpad.net/bzr-explorer/+bug/474812)

I'm about to push the new version to the PPA, but until that update hits you can work around this by manually creating the directory with:

mkdir -p ~/.bazaar/explorer

---

