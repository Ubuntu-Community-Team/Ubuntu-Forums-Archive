---
title: "Sharing folder does not modify smb.conf"
date: 2012-06-28
forum: General Help
---

### Post by timgood on 2012-06-28
Using 12.04 64bit, trying to set up a shared folder on my machine. Samba etc. is installed, but when I define a share it does not modify smb.conf to show. Folder is shown as shared in Nautilus. Trying to access Workgroup results in 'failed to retrieve directory listing' and I can't see any other computers in Workgroup. Any help?

---

### Post by timgood on 2012-06-28
Solution found on 'Ask Ubuntu'

1) Press alt+F2 >> type gksu gedit /etc/nsswitch.conf

2) Look for this line: hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

3) Add "wins" so it looks like this: hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

4) Install the "winbind" package: sudo apt-get install winbind (or via software center or synaptic)

5) Reboot or restart your network

---

