---
title: "knetworkmanager  will not run"
date: 2010-07-01
forum: General Help
---

### Post by ulao on 2010-07-01
I see this is an issue others ran in to, but no remedies. I have tried reinstalling both the kde and the kNetworkManager. I read that I must add the group to my .conf file and that didnt help.

When I select the knetworkmanager in the menu nothing happens. What else can I try.

If I type knetworkmanager  in the terminal same thing happens.
if I type knetworkmanager in a SSH I get "ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting." -- so it must need a GUI to work.

I saw this
> 
Emerge for KDE:

emerge -av kde-misc/knetworkmanager

Add the Runlevels:

rc-update add NetworkManager default
rc-update add dhcdbd default


but neither commands work. I tried  
update-rc.d knetworkmanager add 
but thats not where knetworkmanager, and it nowhere to be found.

---

### Post by ulao on 2010-07-01
Here we go 

 "sudo adduser your_username netdev" needed for debian users, works now..

---

