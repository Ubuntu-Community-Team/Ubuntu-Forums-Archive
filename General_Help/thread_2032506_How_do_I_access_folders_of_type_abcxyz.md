---
title: "How do I access folders of type \\abc\xyz"
date: 2012-07-24
forum: General Help
---

### Post by rambhatm on 2012-07-24
Hi all

So I am not well versed with shares CIFS and such. Generally I mount and access NFS exports via command line.

How can I access folders of type \\abc\xyz? Preferably through nautilus. Before I shifted to ubuntu I could access it though explorer in windows. Anything similar than ubuntu provides?

Also as a supplement can someone give me a background on what these types of shares are. Ive been assuming its a cifs share.

---

### Post by Gyokuro on 2012-07-24
In Nautilus you click on go location and in the location field you enter

smb://server/....

the same for NFS shares. Or you click Browse Network button but sometimes Nautilus have problems to find server/shares.

---

### Post by dino99 on 2012-07-24
check that mountmanager is installed

sudo apt-get install mountmanager

---

### Post by rambhatm on 2012-07-24
> **Gyokuro said:**
> In Nautilus you click on go location and in the location field you enter

smb://server/....

the same for NFS shares. Or you click Browse Network button but sometimes Nautilus have problems to find server/shares.

Cool.. That worked! Thanks

---

