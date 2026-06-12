---
title: "Apache not parsing php in html files"
date: 2010-12-10
forum: General Help
---

### Post by satish_j on 2010-12-10
Hi there,
Can anyone tell me why Apache is not parsing php code inside html files in LAMP?
Whereas the same is working fine in WAMP..

---

### Post by Lone_Joker on 2010-12-10
Apache does not parse PHP from HTML files. Rename your files so that they have a php extension. For example rename index.html to index.php.

If you want Apache to parse HTML files (why would you want this?) I think you could try editing .htaccess
I think you'd have to add this to .htaccess (/var/www/.htaccess I think)

```
RemoveHandler .html .htm
AddType application/x-httpd-php .php .htm .html

```

Another edit. If you don't have that file you can just create it.

---

### Post by satish_j on 2010-12-10
> **Lone_Joker said:**
> 
I think you could try editing .htaccess
I think you'd have to add this to .htaccess (/var/www/.htaccess I think)

```
RemoveHandler .html .htm
AddType application/x-httpd-php .php .htm .html

```

Another edit. If you don't have that file you can just create it.
Already tried this..it is not working..any other ideas..

---

### Post by Lone_Joker on 2010-12-10
What didn't work? The htaccess file? I'm not sure but I think you need to configure apache and htaccess to work together.

But, why don't you just rename your files to have php extensions? You don't need HTML files do you?

---

### Post by satish_j on 2010-12-10
> **Lone_Joker said:**
> What didn't work? The htaccess file? I'm not sure but I think you need to configure apache and htaccess to work together.

But, why don't you just rename your files to have php extensions? You don't need HTML files do you?

I know i can rename the files to get it working,but,as i said it is working fine in Windows environment,i want to know the setting that will enable it in *nix environment.
I doubt whether Apache is looking at this htaccess file.In windows,the setting(AddType) is added in httpd.conf file.Problem is:there is no httpd.conf file for Apache(version 2) in Ubuntu.Documentation says apache2.conf to be used,but there is no such file..
:o

---

### Post by Lone_Joker on 2010-12-10
That's strange. You are checking the /etc/apache2/ directory right? Try running

```
locate apache2.conf
```

I think you could just create the apache2.conf file though.

---

### Post by satish_j on 2010-12-24
Yes,it was the apache2 configuration issue
Added the 'AddType' handler in /etc/apache2.conf it is up and running.

---

