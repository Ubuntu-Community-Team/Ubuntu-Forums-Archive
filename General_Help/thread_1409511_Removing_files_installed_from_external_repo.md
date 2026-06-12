---
title: "Removing files installed from external repo"
date: 2010-02-17
forum: General Help
---

### Post by arnab_das on 2010-02-17
I had added a repo from this site: [http://xdriller.sourceforge.net/downloads.html](http://xdriller.sourceforge.net/downloads.html)

now, i have removed the repo as i dont want to use the software anymore, but how do i make sure that i have removed everything on my pc installed from that repo?

---

### Post by warp99 on 2010-02-17
First remove the software source from your sources list in Synaptic then click Reload. Click on the "Status" button in the left lower section then in the section above click on "Installed (local or obsolete)". All of the packages that were installed from that repository will be listed here. Just highlight the ones you want to remove then right mouse click and choose "Mark for Complete Removal". All of the files, including configuration files, for that package will be removed.

---

### Post by arnab_das on 2010-02-17
> **warp99 said:**
> First remove the software source from your sources list in Synaptic then click Reload. Click on the "Status" button in the left lower section then in the section above click on "Installed (local or obsolete)". All of the packages that were installed from that repository will be listed here. Just highlight the ones you want to remove then right mouse click and choose "Mark for Complete Removal". All of the files, including configuration files, for that package will be removed.

thanks mate. that worked. :)

---

