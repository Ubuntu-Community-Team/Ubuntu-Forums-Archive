---
title: "change directory not working?"
date: 2009-12-24
forum: General Help
---

### Post by Scooter_X on 2009-12-24
Hey how in the heck do I change to the directory /media/data storage (data storage is a different partition that I mounted for dual-boot purposes) but when I try in the terminal to: 

cd /media/data storage

it says: 

no such directory: /media/data

and leaves it at that. i tried using /media/data_storage and /media/datastorage but neither work... I don't get it. Why does it do that? Any help greatly appreciated. Thanks!

---

### Post by taurus on 2009-12-24
Either one should work.

```
cd "/media/data storage"
-or-
cd /media/data\ storage
```

You need to use " " when there is a space between the name.

---

### Post by Scooter_X on 2009-12-24
Ha! Thanks a bundle!

---

