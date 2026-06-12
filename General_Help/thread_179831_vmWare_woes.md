---
title: "vmWare woes"
date: 2006-05-20
forum: General Help
---

### Post by iand675@gmail.com on 2006-05-20
I've brought my grandpa over to linux, but he still wants windows in case he needs it for some reason. I've gotten vmWare workstation installed, and need to transfer some files onto the virtual windows drive. Any suggestions?

---

### Post by rugge on 2006-05-20
Do you have networking on your virtual Windows machine?

Rutger

---

### Post by iand675@gmail.com on 2006-05-20
yeah it has a bridged connection

---

### Post by crashtest on 2006-05-20
You could run an ftp server on the host machine and connect to it from the guest machine.  You could also run a samba server on the host, and connect to that from the guest.  Yet another way would be create a network share on the Windows guest machine, and do a smbmount on the Linux host machine.  Probably other methods I'm not thinking of as well.

---

### Post by rugge on 2006-05-21
Yes that was my thought too! :) 
Or the other way around. There are small freeware FTP and TFTP servers out there for windows.

Kind regards,
Rutger

---

