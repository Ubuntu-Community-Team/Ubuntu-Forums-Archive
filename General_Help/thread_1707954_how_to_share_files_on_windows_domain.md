---
title: "how to share files on windows domain?"
date: 2011-03-16
forum: General Help
---

### Post by xirochanh on 2011-03-16
I installed ubuntu 10.10 on a machine in office. I like to use this machine for file sharing on windows domain, all other client machines are windows, domain controller is windows server 2008.
I installed likewise, can join domain now, so far, I just can log-in this ubuntu by domain users, don't know what I can do next.
I installed samba as well, can share files for windows clients to access with setting: everyone to read.

How could I make it able to authenticated windows domain accounts?
I'm confusing about likewise open & winbind: samba with winbind only, or just likewise without samba can help, or must use samba plus winbind & likewise.

Any comment is highly appreciated

---

### Post by Script Warlock on 2011-03-16
this might help.. [http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-vista-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/enable-file-sharing-windows-vista-ubuntu-10-10-maverick-meerkat/)

---

### Post by xirochanh on 2011-03-16
Thank bro,

I can do like that tutorial, but my situation requires more: domain account authentication/permission on shared folders

---

