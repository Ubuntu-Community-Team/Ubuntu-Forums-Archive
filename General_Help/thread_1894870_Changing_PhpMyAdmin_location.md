---
title: "Changing PhpMyAdmin location"
date: 2011-12-13
forum: General Help
---

### Post by mrnothersan on 2011-12-13
Hello

Is it possible to change the default phpmyadmin location from domain.com/phpmyadmin to something different?

Regards
Dominic

---

### Post by lechien73 on 2011-12-13
phpmyadmin creates a symbolic link from /var/www/phpmyadmin to /usr/share/phpmyadmin

So you can change the location by typing:

```
sudo ln -s /usr/share/phpmyadmin/ /var/www/newlinkaddress
```

You can then remove the previous link:

```
sudo ulink /var/www/phpmyadmin
```

---

### Post by mrnothersan on 2011-12-13
> **lechien73 said:**
> phpmyadmin creates a symbolic link from /var/www/phpmyadmin to /usr/share/phpmyadmin

So you can change the location by typing:

```
sudo ln -s /usr/share/phpmyadmin/ /var/www/newlinkaddress
```

You can then remove the previous link:

```
sudo ulink /var/www/phpmyadmin
```

Great reply, thank you!

---

### Post by lechien73 on 2011-12-14
> **mrnothersan said:**
> Great reply, thank you!

You're welcome :) if the issue is now resolved, could you please mark it as [SOLVED] using the **Thread Tools** menu at the top of the page?

Thanks

---

