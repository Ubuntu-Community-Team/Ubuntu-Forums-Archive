---
title: "Flash shared object editor for ubuntu?"
date: 2011-05-17
forum: General Help
---

### Post by dragonfly41 on 2011-05-17
I've used shared object editors in windows .. shared object is a cookie to pass information between flash objects and javascript.

Are there any shared object editors for ubuntu?

And where do shared object files reside in ubuntu?   In windows they have extension*.so

---

### Post by dragonfly41 on 2011-05-17
From reading this .. [http://tips.webdesign10.com/flash-cookies-privacy](http://tips.webdesign10.com/flash-cookies-privacy)

I've tracked down where the Flash sharedobjects reside

```
~/.macromedia/Flash_Player/#SharedObjects/<random_name_folder>/ 
```

they end with *.sol extension
one folder per domain visited .. or cookie planted
but what ubuntu editor can open these files?

...

Some users just change the permissions on this #SharedObjects folder to block planting of cookies

chmod 000

but I want to use shared objects as in Red5 style to pass information between flash objects.

---

