---
title: "apache 2"
date: 2011-01-11
forum: General Help
---

### Post by na2el on 2011-01-11
hi everyone,  how to configure apache2 so i can save my html and php files in the www folder because when i type [http://localhost/mywebsite.php](http://localhost/mywebsite.php) it gives an error: not found The requested URL /mywebsite.php was not found on this server.

---

### Post by WorMzy on 2011-01-11
Just use chown to gain ownership of the folder.

Open a terminal (Applications -> Accessories -> Terminal) and paste this command into it:

```
sudo chown $USER:$USER /var/www
```

Press Enter to execute the command, and then enter your password when prompted.

After that you can add/edit/delete files in the folder. However, don't use that command on other folders, or you could end up breaking your Ubuntu installation.

---

### Post by hawkmage on 2011-01-11
Depending on the permissions on the folders/files that may break Apache.  If Apache can not read the files because of the ownership change.  By default the user and group for Apache installed on Ubuntu is www-data.

---

