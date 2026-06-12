---
title: "Problem with chmod"
date: 2011-06-19
forum: General Help
---

### Post by kozenko on 2011-06-19
Hello guys,
I have changed permissions of /opt with this cmd:
```
sudo chmod -Rf 777 /opt
```
But now, google chrome (that is intalled in /opt) doesnt launch.

Do you know how to put it back to normal permissions.


PS: I did it becouse I wanted to access to XAMPP folder.


Thanks,
Koz

---

### Post by kozenko on 2011-06-22
75 views no answers? =S

---

### Post by maidenfan on 2011-08-25
If you know the original permissions, just change them back to orig using chmod.
Did your original command work ? Did it change the permissions of /opt ?

---

### Post by fdrake on 2011-08-25
> **maidenfan said:**
> If you know the original permissions, just change them back to orig using chmod.
Did your original command work ? Did it change the permissions of /opt ?

you can try by resetting back the permissions

```

sudo chmod -R 732 /opt
sudo chmod -R 777 /opt/<xampp folder's name>

```
note :  777 permission is very risky. use it only for test purposes only, in a local network...

---

### Post by jfed on 2011-08-25
you could un-install then re-install chrome, then perhaps change mod it with a different argument

---

