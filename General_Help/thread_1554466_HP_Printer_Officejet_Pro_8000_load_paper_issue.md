---
title: "HP Printer Officejet Pro 8000 load paper issue"
date: 2010-08-16
forum: General Help
---

### Post by paddydd on 2010-08-16
Hi,
  I have a HP Officejct Pro 8000 Printer hooked to UBUNTU 9.10 on a system 76 box. The printer is not loading paper properly. I see references to this issue on various websites and I saw at least one reference to new drivers but alas they were all for windows. I checked the repository and I have the latest and greatest HPLIP. Does this mean I have all of the latest drivers?

Has anyone seen this issue? I need some guidance please.
 

Thanks
Paddy

---

### Post by bartek2 on 2011-02-05
I have the same printer and it doesn't have any problem on Ubuntu 10.04 LTS. Try to upgrade to 10.04 or type in the terminal:
```
hp-setup
```or
```
sudo apt-get hp-toolbox
```  and try to check what's going on
or 
try to upgrade to hplip 3.10.2 which i'm using

---

### Post by paddydd on 2011-02-06
Thanks for the thought.

I should have posted this earlier but the solution was fpr HP to send us a replacement.

The printer now works.

Paddy

---

