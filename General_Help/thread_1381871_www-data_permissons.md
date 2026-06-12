---
title: "www-data permissons"
date: 2010-01-15
forum: General Help
---

### Post by gazz1982 on 2010-01-15
Hi I'm using ubuntu with Apache, apache is root user group I need it to be www-data group but www-data group doesnt exist, how can I fix this?

Thanks

---

### Post by mk1w86 on 2010-01-15
To add a group use the groupadd command.  For more information run:

```
man groupadd
```

There is also an addgroup command which is the low level utility for adding groups but it is recommended you use the above command, not this one. ;)

---

