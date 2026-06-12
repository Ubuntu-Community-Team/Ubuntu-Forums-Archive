---
title: "debconf broken? (Karmic x86_64)"
date: 2009-12-03
forum: General Help
---

### Post by petronio on 2009-12-03
Right now I'm on a Karmic x86_64 with the 2.6.31-15-generic kernel.
 
When trying to install samba 2:3.4.0-3ubuntu5.2_amd64 I get the following error (and other errors relating to that error):
 
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
and follows to exit with error code 1.
 
After further investigation the reason it could not open that file is because the file does not exist. 
 
apt-get reports debconf as the latest version and any trials to dpkg-reconfigure debconf in order to fix the error causes the error to come up again (oh the irony).
 
Anybody have any thoughts?
 
(If anybody was wondering, I have karmic-proposed activated)
 
On a side note: For some reason I don't have Grub 2 (mabey because I upgraded from 9.04?) and any trials to install it gives me the debconf error.

---

