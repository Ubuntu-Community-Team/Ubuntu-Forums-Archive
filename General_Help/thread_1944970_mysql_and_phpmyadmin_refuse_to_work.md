---
title: "mysql and phpmyadmin refuse to work"
date: 2012-03-22
forum: General Help
---

### Post by surrealillusions on 2012-03-22
Hi,

I'm having some trouble trying to set up mysql and phpmyadmin on the computer.

I have apache and php setup - they're working fine.

Whenever I go to localhost/phpmyadmin, I cant login. It wont accept the password, and when I try without a password it says:

"Login without a password is forbidden by configuration (see AllowNoPassword)"

I've tried searching around on Google for steps to recover or change the password, but whatever I try, it wont. Either it cant find a mysql process to stop or cant find any relevant files to change.

I've tried removing all mysql from the synaptic manager, and installing again, but to no avail. When going to uninstall, it asks for a password to delete data, but I dont know the password!

What I would like to do, is completely flush the system of any mysql/phpmyadmin and settings, and set it up again from scratch. There's no data in the databases that I know of, and if there is, I'm not using it anyway in any site development.

Is there anyway of solving this?

Thanks.

---

### Post by hansum_rahul on 2012-03-22
You need to rerun the install, try the following:

```
sudo dpkg-reconfigure mysql-server-* phpmyadmin
```

---

### Post by surrealillusions on 2012-03-22
Thanks.

Seems mysql-server was missing, installed that and I've managed to reset the password.

---

