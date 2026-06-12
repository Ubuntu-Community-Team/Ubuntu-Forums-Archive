---
title: "Ubuntu Update Manager Error Message"
date: 2011-06-08
forum: General Help
---

### Post by ZaydHumsy on 2011-06-08
[FONT="System"][/FONT] When I "Check" for updates in the Ubuntu Software Center the progress bar gets to about 4/5 of the way and gives me this error message "Failed to download repository information" 
 
Under 'details' in gives me this: 
"W:Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found 
, W:Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found 
, E:Some index files failed to download. They have been ignored, or old ones used instead."

Any suggestions?

---

### Post by drs305 on 2011-06-08
That server appears to be down. You can open Synaptic or Software Sources, then Settings > Repositories > Other Software tab and untick the lorenzo-carbonell" entries. Hit reload and it should update without errors.

If you have used this repository before it may just be down at the moment. You can reselect it later to see if it's come back online.

---

