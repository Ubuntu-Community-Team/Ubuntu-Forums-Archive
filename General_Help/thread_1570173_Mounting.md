---
title: "Mounting"
date: 2010-09-07
forum: General Help
---

### Post by FahadMKS on 2010-09-07
Can anyone tell me how to mount an ISO image on my downloads folder manually using commands.

---

### Post by Smart Viking on 2010-09-07
first you might want to create a location to mount it:
```
sudo mkdir /media/mount
```
Then mount it there using this:
```
sudo mount -o loop /location/to/image.iso /media/mount
```
Hope this helps. :)

---

### Post by Calaway21 on 2010-09-07
Read the mount man page. You can find the information there.

---

### Post by FahadMKS on 2010-09-10
Thanks Guys.

That worked.

---

