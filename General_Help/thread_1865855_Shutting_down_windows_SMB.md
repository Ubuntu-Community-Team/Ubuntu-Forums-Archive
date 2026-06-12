---
title: "Shutting down windows SMB"
date: 2011-10-20
forum: General Help
---

### Post by jamessceptre on 2011-10-20
How does one shut down smb in ubuntu 11.10
I wish to block ubuntu from seeing other computers and shared folders on the network

---

### Post by gandaran on 2011-10-20
should be easy, install the firewall gui 'gufw' and block the SMB ports

---

### Post by duke.tim on 2011-10-20
You could always block the samba ports


Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd

Use gufw, unlock, add etc...

---

### Post by jamessceptre on 2011-10-20
Thanks for the help worked perfect

---

