---
title: "Problem with Samba"
date: 2009-09-05
forum: General Help
---

### Post by AccoladeNZ on 2009-09-05
I am having an issue with Samba. I believe that everything is working as it should, however I am unable to access the share properly from my local machine.

I am running ubuntu server 9.04 in a VM on a dedicated server running Windows 2k3. I have two static IPs running off of 1 NIC. I suspect that this may be causing the issue. What I want to do is run an FTP server from my windows machine accessing files from my ubuntu VM. 

The frustrating thing is, I believe that my smb.conf is fine, I have tried every possible different combination and it all appears to work (I can see the server in 'My Network Places' under the correct workgroup. But whenever I do a \\servername\share or \\IP\share it denies me with the following message:

'No network provider accepted the given network path.'

I have given this a solid google and good go at trying to fix, anyone have any ideas? I have played around with IPtables disabling the firewall, changed the netmasks of both machines so they can see one another in the workgroup. I also get a similar issue trying to connect webdavs from the Windows 2k3 local machine to the ubuntu VM, and yet I can connect them from an external IP to the ubuntu VM.

Puzzler! :)

---

### Post by AccoladeNZ on 2009-09-05
Here is my smb.conf:

[global]
workgroup = WORKGROUP
netbios name = myubuntuserver
security = share

[Share1]
path = /usr/local/accoladenz/
available = yes
writable = yes
guest ok = yes
browsable = yes

.........

I can confirm that I am able to access \\IP\Share1\ from an external IP just not the IP of my Windows 2003 machine running the ubuntu VM. Possibly a Windows networking issue?

---

