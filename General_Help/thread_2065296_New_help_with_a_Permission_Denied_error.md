---
title: "New help with a Permission Denied error"
date: 2012-10-01
forum: General Help
---

### Post by rlischer on 2012-10-01
I am running Ubuntu 12.04 on Amazon EC2 and trying to get email working. I was told during the install to enter:

```
echo 1 > /etc/pure-ftpd/conf/TLS
```

but I get a Permission denied every time, I also tried using sudo with no luck.  Any ideas?

Thanks

---

### Post by funicorn on 2012-10-01
Keep in mind that 'pipe'  knows nothing about permission, and sudo doesn't work on a pipe. so use
echo 1 |sudo tee /etc/pure-ftpd/conf/TLS

---

### Post by rlischer on 2012-10-01
> **funicorn said:**
> Keep in mind that 'pipe'  knows nothing about permission, and sudo doesn't work on a pipe. so use
echo 1 |sudo tee /etc/pure-ftpd/conf/TLS

Thanks!  That worked!

---

