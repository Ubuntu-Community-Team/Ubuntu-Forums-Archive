---
title: "Unable to access NAS"
date: 2011-04-29
forum: General Help
---

### Post by Rodayo on 2011-04-29
Hi all,

I recently purchased an Iomega home network storage. Product page:

[http://go.iomega.com/en-us/products/network-storage-desktop/home-network-hard-drives/home-media/?partner=4760](http://go.iomega.com/en-us/products/network-storage-desktop/home-network-hard-drives/home-media/?partner=4760)

While I was using Natty Beta 2, I just installed samba4 and it would show up under 
Network>Workgroups>IOMEGA...

Once I freshly installed the final release of Natty it's no longer working. 

I can see the NAS as on my router's config page and it's readily available on my windows machine so that's not the issue.

Does anyone know what the problem could be?

Edit: 
Solved the issue by adding a cifs mount entry to fstab like so:

192.168.1.72:/share    /mnt/nas    cifs    password=PASSWORD    0    0

---

