---
title: "tmp or temp assigned elsewhere"
date: 2010-10-01
forum: General Help
---

### Post by nutellajunkie on 2010-10-01
is it possible to have the tmp or temp folders assigned elsewhere. I am actually looking to stick them in the shm folder since there is enough memory to throw around the place :)

Thanks in advance.

---

### Post by psusi on 2010-10-01
If you want /tmp to be stored in ram, then mount it as a tmpfs.  Add this line to your /etc/fstab:

tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

---

