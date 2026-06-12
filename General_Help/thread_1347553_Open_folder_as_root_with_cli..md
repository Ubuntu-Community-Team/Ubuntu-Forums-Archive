---
title: "Open folder as root with cli."
date: 2009-12-06
forum: General Help
---

### Post by _sAm_ on 2009-12-06
I need to open the folder; /var/lib/geneweb/ via cli, but I cant as a normal user(Permission denied
). How can I open it without changing the permission? sudo cd geneweb didnt help.

---

### Post by IllegalCharacter on 2009-12-06
What does sudo ls /var/lib/geneweb/ give you?

---

### Post by SuperSonic4 on 2009-12-06
```
sudo cd /var/lib/geneweb/
```

```
ls -A
```

---

### Post by _sAm_ on 2009-12-06
> **SuperSonic4 said:**
> ```
sudo cd /var/lib/geneweb/
```

```
ls -A
```
Command "sudo cd /var/lib" gives me;
sudo: cd: command not found

The command;"sudo ls /var/lib/geneweb/" worked. 

Thanks:-)

---

### Post by aysiu on 2009-12-06
```
sudo -i
``` is a quick way to get temporary root access.

---

### Post by _sAm_ on 2009-12-06
Thanks again aysiu:-)

---

