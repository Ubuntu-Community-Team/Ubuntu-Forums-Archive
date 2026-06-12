---
title: "Changing permissons"
date: 2012-08-04
forum: General Help
---

### Post by garyzw on 2012-08-04
How would I change the permissions of a folder and all the files in that folder from root to owner? I can do it individually for each file but that seems time consuming.

---

### Post by steeldriver on 2012-08-04
To change permissions you would use chmod - but it sounds like you want to change the *ownership* 

```
chown -R *user* dir
```
or to change owner and group (probably what you want)

```
chown -R *user*:*user* dir
```

---

### Post by garyzw on 2012-08-04
That worked! Thanks a million!

---

