---
title: "Is there a username limit for linux/ubuntu?"
date: 2011-06-06
forum: General Help
---

### Post by ingramproductions on 2011-06-06
Is there a username limit (like 16 or 256 characters) for linux/ubuntu? If so, what is the limit?

---

### Post by Toz on 2011-06-06
According to ```
getconf LOGIN_NAME_MAX
``` the maximum length is 256. However, I believe that libc-6 has an upper limit of 32

From **man useradd**:
> Usernames may only be up to 32 characters long.

32 it is then.

---

### Post by ingramproductions on 2011-06-12
Thanks

---

