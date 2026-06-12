---
title: "Ubuntu VM + Samba running on Windows 2003 = Not working"
date: 2009-09-05
forum: General Help
---

### Post by AccoladeNZ on 2009-09-05
I am running Windows 2003 R2 and I am unable to access Samba shares running on a Ubuntu VM on the same machine. The local machine (Win2k3) and the VM (Ubuntu 9.04) both have unique static IPs running off the same NIC and both are in the same workgroup with the same netmask. I can see the netbios name in 'View workgroup computers' and I am able to access this samba share from my WindowsXP SP3 machine from an external IP. However when I attempt to access the share either by using \\COMPUTERNAME\share or \\IP\share or by double clicking on the netbios name in My Network Places -> View Workgroup, I get the following error:

No network provider accepted the given network path.

This is certainly not an issue with the linux side of things (as I am able to access these shares from external Windows XP machines. I believe this is an issue with either Windows 2003 networking or group policy. Can someone please help?

---

