---
title: "Update manager not updating"
date: 2010-11-19
forum: General Help
---

### Post by cyberjar09 on 2010-11-19
Im not sure why this is happening ...but update mgr is not updating saying that "requires installation of untrusted packages" 

find screenshots attached

update manager where text is not clearly visible says 

"W:Failed to fetch [http://android-notifier.googlecode.com/svn/repos/deb-repo/dists/stable/main/source/Sources.gz](http://android-notifier.googlecode.com/svn/repos/deb-repo/dists/stable/main/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead." 

I do have internet connectivity so whats the problem?

Ubuntu 10.10

---

### Post by Joeb454 on 2010-11-19
It looks like the 'android-notifier' repository has been moved, or is currently down. I say this as the first part of the error message says 'Some index files failed to download'.

Try commenting out that repository, or unticking it through update-manager settings.

---

### Post by cyberjar09 on 2010-11-19
I just uninstalled it completely ...

sweet... working now .. downloading the updates! 

thanks! =D

---

