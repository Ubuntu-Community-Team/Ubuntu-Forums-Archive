---
title: "problem with vmware console plugin, roll back gtk??"
date: 2009-10-25
forum: General Help
---

### Post by sdowney717 on 2009-10-25
[http://communities.vmware.com/thread/235572?tstart=0](http://communities.vmware.com/thread/235572?tstart=0)

this is what i have been experiencing. 
they say it is a problem with gtk
how would you roll back to earlier versions?


> [http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=63219.0](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=63219.0)

Apparently there is some sort of change in these packages that cause problems with the plugin. This problem is effected by Kubuntu 9.10 as well (after all updates).

Apparently rolling back fixes the mouse focus problem.

gtk+2.0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgdk_pixbuf2.0_0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgtk+-x11-2.0_0 (version 2.18.1-1pclos2009) downgraded to version 2.16.6-3pclos2009
libgtk+2.0_0 (version 2.18.1-1pclos20092.16.6-3pclos2009) downgraded to version 2.16.6-3pclos2009

---

