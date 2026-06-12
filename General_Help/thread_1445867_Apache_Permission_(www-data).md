---
title: "Apache Permission (www-data)"
date: 2010-04-03
forum: General Help
---

### Post by OOzypal on 2010-04-03
Hello,

I am having some problems understanding the apache permission. I changed the ownership of all my web files to www-data
```
 chown -R www-data.www-data mysite
```
Now I cannot write to the files i.e. when I click save in Aptana it gives me an error of permission denied. 

Can someone shed some light on this issue. 

OOzy

---

### Post by rudy.b on 2010-04-03
It depends on how you have your permissions set up, but likely you have write permission for the owner only.  Which means that only the user www-data can write to the files/directories in mysite, so you won't be able to edit those files unless you elevate your privileges to root (i.e. using sudo or gksudo).

Generally, I would set the ownership for web files as follows:  ```
$ sudo chown -R ownerid:www-data mysite
```Since Apache doesn't usually need write permissions for the web files (although there are exceptions such as file upload directories), it's safe to restrict write permissions to the owner only.

---

