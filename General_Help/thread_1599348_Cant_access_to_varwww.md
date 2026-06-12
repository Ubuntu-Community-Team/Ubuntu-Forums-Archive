---
title: "Cant access to var/www"
date: 2010-10-17
forum: General Help
---

### Post by Lancro on 2010-10-17
Im Trying to use apache with php and MySql, LAMP, when I try to copy files to this directory, it doesnt allow me to do, I tried to change the permisions for the folder, but It tolds me that only root can access...

I installed ubuntu using the windows installer, it asked me for a user and a password, nor for root password, I tried to login as root with same password, but it doesnt allow me to login, is there any default password for my instalation?, where the hell is that password, please help me, excuse my english, Im spanish.

Thanks.

---

### Post by Lancro on 2010-10-17
I have changed my account from user to administrator, but same results, please anyone helps.

Thanks.

---

### Post by WorMzy on 2010-10-17
Easiest solution:
```
sudo chown $USER /var/www
```

---

### Post by Lancro on 2010-10-17
> **WorMzy said:**
> Easiest solution:
```
sudo chown $USER /var/www
```

solved...

Thanks.

---

### Post by davrosuk on 2010-10-17
Isn't that directory normally root:www-data by default? If so you can just make your user a member of the www-data group. I'm fairly sure thats what I've done previously.

---

