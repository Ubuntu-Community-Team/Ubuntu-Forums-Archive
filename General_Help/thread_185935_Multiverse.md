---
title: "Multiverse"
date: 2006-06-01
forum: General Help
---

### Post by tom56 on 2006-06-01
I just noticed that there doesn't seem to be an option for multiverse in "Software Properties" in my virgin Dapper install. Is that meant to be like that? Seems a little odd to me.

---

### Post by johnc4510 on 2006-06-01
I don't know where "software properties" is. 
To enable extra repositories including universe and multiverse do this:
System>Administration>Synaptic Package Manager
Click on settings, then click on repositories
Put a check mark in all the empty boxes
Close that window and click on:Reload, then Mark all Upgrades, then Apply
Now all repositories should be enabled

---

### Post by tom56 on 2006-06-01
That *is* "Software Properties"

---

### Post by tom56 on 2006-06-01
Bump. Anyone?

---

### Post by pelle.k on 2006-06-01
no but go ahead and add it yourself;
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse

---

