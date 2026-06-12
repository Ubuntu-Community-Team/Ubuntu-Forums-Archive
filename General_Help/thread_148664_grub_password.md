---
title: "grub password?"
date: 2006-03-22
forum: General Help
---

### Post by njzillest on 2006-03-22
how can i put a password to lock my grub?

thanks in advance

---

### Post by lotheac on 2006-03-22
First, run grub in a terminal. Then use grub's md5crypt command and type in your password - we do this because you don't want your password to be in plaintext in the configuration file. Take the output of the command and edit /boot/grub/menu.lst accordingly.

```
$ grub
grub> md5crypt
Password: 12345
Encrypted: $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
grub> quit
```

Here's the relevant part in menu.lst:
```
password --md5 $1$OYbzL1$vzQPe4kkqJl/htEhKfCjS1
```

---

