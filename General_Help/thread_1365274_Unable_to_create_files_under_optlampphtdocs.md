---
title: "Unable to create files under /opt/lampp/htdocs"
date: 2009-12-27
forum: General Help
---

### Post by cancer10 on 2009-12-27
Hi

I installed XAMPP under unbuntu last night and the installation was successful.

However, I cannot edit any files under /opt/lampp/htdocs nor can i create any files under that directory.

Does anyone know Whats happening?


Thanks

---

### Post by john newbuntu on 2009-12-27
Those files and directory are probably owned by root.  You need to use the "sudo " prefix to modify or add files.  You could even change the user and group id on that directory.

The other alternative would be to set up a different directory to serve web pages from, which would involve copying the /etc/apache2/sites-available/default file to another.  You would then deactivate the existing site and reactivate the new one.  For more info, search for "a2dissite" in this documentation:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by cancer10 on 2009-12-27
> **john newbuntu said:**
> Those files and directory are probably owned by root.  You need to use the "sudo " prefix to modify or add files.  You could even change the user and group id on that directory.

The other alternative would be to set up a different directory to serve web pages from, which would involve copying the /etc/apache2/sites-available/default file to another.  You would then deactivate the existing site and reactivate the new one.  For more info, search for "a2dissite" in this documentation:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)



How do I login as a root to my system?

---

### Post by john newbuntu on 2009-12-27
If you normally use 'gedit', you will have to use 'gksudo edit'.  If you use vi then you would do a 'sudo vi'

---

### Post by avl555 on 2009-12-27
The root account is the "administrator" of the system. The username is 'root' and the password is given by installation (or changed if you have changed the root password).

The easiest way is to change the user of the directory /opt/lampp/htdocs:
```
sudo chown username /opt/lampp/htdocs
```Change username to your username.
This is (in my opinion) the easiest option for your own use, but not a good option for a real web server (outside your computer).

You can also log in as root, but that could be dangerous! As root, you have total control over the system, and you can accidentally delete files and do other dangerous things you don't want. So DON'T use it.

And you can also, as john newbuntu said, change the root directory of the web server (root means the base directory, in this case).

---

