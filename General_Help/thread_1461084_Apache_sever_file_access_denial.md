---
title: "Apache sever file access denial"
date: 2010-04-23
forum: General Help
---

### Post by stratex1 on 2010-04-23
Hi everybody,
i have ubuntu 9.10 and apache 2 installed. My documents folder is /var/www
I can access index.php which is under www folder or any other "main" file as index.php or index.html in subdirectories as www/example/index.html but any other file in subdirectories cant be accessed The same any file (as an image) called from a subdirectory in the main file will not be displayed.
Example: if from /www/example/index.html page I click a link which should redirect me to:
/www/example/html/test.html I get a forbidden message:
You don't have permission to access /html/test.html on this server.
Thanks for help in advance.
Julian

---

### Post by cariboo on 2010-04-23
Check directory permissions and ownership on my system, every thing is owned by www-data or root. Permissions are 755 except for the default index file which for some reason has a permission of 644.

You can generally set ownership my by typing at the prompt:

```
sudo chown -R www-data:www-data <dirname>
```

where <dirname> is the name of the directory you want to change ownership on. For permissions:

```
sudo chmod -R 755 <dirname>
```

The -R sets the ownership and permissions recursively.

---

