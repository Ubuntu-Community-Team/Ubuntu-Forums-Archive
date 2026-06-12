---
title: "why this error"
date: 2012-09-14
forum: General Help
---

### Post by Mohan1289 on 2012-09-14
when i typed the command "apt-get update" it's showing following errors can you tell me why?
 
[http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
  404  Not Found
Get:7 [http://mirror1.ku.ac.th](http://mirror1.ku.ac.th) quantal/universe amd64 Packages [5,327 kB]       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
  404  Not Found

---

### Post by sanderj on 2012-09-14
Both URLs work for me, so I would say a bad Internet connection (or DNS) on your side ...

Easy way to check: can you click on the URLs you posted ... ?

---

### Post by plucky on 2012-09-14
> **sanderj said:**
> Both URLs work for me, so I would say a bad Internet connection (or DNS) on your side ...

Easy way to check: can you click on the URLs you posted ... ?

It is more likely that there is no PPA for Quantal Quetzal repository.Both those links point to the PPA Index on Launchpad.

Open Software Sources and un-tick the PPAs and then try the update again.

Good luck

---

### Post by Mohan1289 on 2012-09-14
Thank you

---

### Post by oldos2er on 2012-09-14
Quantal is beta, and should only be run for testing purposes. Its forum is here: [http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416) and all discussion concerning Quantal should be posted there.

---

