---
title: "Samba GUI Shares"
date: 2009-08-12
forum: General Help
---

### Post by mpsrig on 2009-08-12
Hi everyone,
For samba shares made using the Ubuntu GUI, it seems the share information is not stored in smb.conf.  Could someone point me to it?

The reason I am asking is because I want to share root over samba (yes i know the risks, i have reasons for doing it, its behind a hardware firewall) and so rather than having both smb.conf and the other mysterious file above littered with share info, I would like to add it to the same place Nautilus does.

---

### Post by Iowan on 2009-08-12
Does [this]("http://ubuntuforums.org/showthread.php?t=1176404") one help? Seems like there is another place, but I don't remember where (/var/lib/...?)

---

### Post by mpsrig on 2009-08-13
I think you don't understand my request.  I assume that shares setup through natilus are also recorded in a conf file for samba to load.  I wish to find that conf file as it is not the same as smb.conf

---

### Post by CrusaderAD on 2009-08-13
I'd be interested in finding this too. Once you map a share with the ubuntu gui, it seems it's there permanently.

---

### Post by mpsrig on 2009-08-13
I am talking about local folders set up to be shared over samba, not shares mounted over samba.

---

