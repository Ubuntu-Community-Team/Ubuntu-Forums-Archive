---
title: "Mount Help!"
date: 2010-10-01
forum: General Help
---

### Post by TaekOnai on 2010-10-01
Hi folks, i'm looking for a way to mount a local file dir using fstab, right now i am using mount -bind and it works, but if i need to restart i haveto run it everytime.

So if anyone has any ideas!

---

### Post by sisco311 on 2010-10-01
The fstab entry should look like this:
```
/olddir /newdir none bind
```

See:
```
man mount | less +/"The bind mounts."
```

---

