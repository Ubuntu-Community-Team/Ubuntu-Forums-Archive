---
title: "mount -t cifs only root can do that"
date: 2009-06-30
forum: General Help
---

### Post by mbeierl on 2009-06-30
Ok, I've been beating my head against the wall for some time now.  Why is it that every time I attempt to use mount -t cifs, I always get the infamous:
```

$> mount -t cifs //server/home test 
mount: only root can do that

```

mount.cifs is setuid, so I'm puzzled:

```

-rwsr-sr-x 1 root root 32088 2009-03-27 15:40 /sbin/mount.cifs

```

What am I missing?

---

### Post by 3rdalbum on 2009-06-30
What happens when you substitute "mount" for "pmount"?

---

### Post by mbeierl on 2009-06-30
Nothing useful, I'm afraid:

```

pmount -t cifs //serve/home /test
Error: could not determine real path of the device: No such file or directory

```

---

### Post by mbeierl on 2009-07-02
Ok, so there appears to be no difference between mount -t cifs and mount.cifs, just that mount is a front end and can only be executed by root.  Unless someone can contradict me, I'm closing this as my own ignorance :)

---

