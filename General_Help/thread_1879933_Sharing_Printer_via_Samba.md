---
title: "Sharing Printer via Samba"
date: 2011-11-12
forum: General Help
---

### Post by crutch145 on 2011-11-12
I have a local HP printer attached to my Ubuntu system.  I am running 11.10.  Using Samba, when I click on + sign to add a Samba share, how can I find my printer from that point?  I want to share this printer with Windows clients. 

Thanks,

Justin

---

### Post by Morbius1 on 2011-11-12
> Using Samba, when I click on + sign to add a Samba share, how can I find my printer from that point?You don't. Well I suppose you can, but samba is set up to be a pass-through to cups.

So in Ubuntu:
Bring up the Printer utility and for that printer make sure the the following is enabled: **Shared**

Still in the same utility selsect > Server > Settings and make sure the following is enabled: Publish shared printers connected to this system.

Then edit smb.conf to allow guest access by changing "guest ok" to yes:
> [printers] 
   comment = All Printers 
   browseable = no 
   path = /var/spool/samba 
   printable = yes 
[COLOR=Blue]   guest ok = yes [/COLOR]
   read only = yes 
   create mask = 0700Then restart the following services in this exact order:
```
sudo service cups restart
sudo service smbd restart
```Then run the following command to see if you can see your own networked printer:
```
smbtree
```

---

