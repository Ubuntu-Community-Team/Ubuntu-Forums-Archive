---
title: "apache 2 setup (403 errors)"
date: 2011-01-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-01-21
i sym linked my /var/www to /home/$USER/.public_html
so i do not have to be root to edit my pages
i added www-data to my group and lp
any ideas on how to get rid of the 403 errors?
edit:
what should i install so ftp will work

---

### Post by Wtower on 2011-01-21
Haven't ever tried but I believe there is a configuration option called FollowSymLinks that can go in the httpd.conf or .htaccess files. Be much careful for security issues.

---

### Post by pqwoerituytrueiwoq on 2011-01-21
where is httpd.conf at?

---

### Post by ubudog on 2011-01-21
> **pqwoerituytrueiwoq said:**
> where is httpd.conf at?

I believe it is at /etc/apache2/httpd.conf, but I may be mistaken.

---

### Post by pqwoerituytrueiwoq on 2011-01-21
is there but file is blank

---

### Post by CharlesA on 2011-01-21
> **ubudog said:**
> I believe it is at /etc/apache2/httpd.conf, but I may be mistaken.

That's correct.

> **pqwoerituytrueiwoq said:**
> is there but file is blank

It is an empty file by default.

You could do it like I did and set up a virtualhost instead of using symlinks. Might not be the best way to do it, but it worked for me.

---

### Post by ubudog on 2011-01-21
> **CharlesA said:**
> That's correct.



It is an empty file by default.

You could do it like I did and set up a virtualhost instead of using symlinks. Might not be the best way to do it, but it worked for me.

VirtualHosts should work.

---

### Post by pqwoerituytrueiwoq on 2011-01-21
sym linking to ntfs partition works
how can i link to my home partition and have it work
encrypted folder but it should work if i am logged in

---

### Post by CharlesA on 2011-01-21
> **pqwoerituytrueiwoq said:**
> sym linking to ntfs partition works
how can i link to my home partition and have it work
encrypted folder but it should work if i am logged in

It should work, yes.

You can add something like this to httpd.conf

```
<VirtualHost *:80>
DocumentRoot /path/to/folder/
</VirtualHost>

```

Then restart Apache:

```
sudo service apache2 restart
```

---

### Post by pqwoerituytrueiwoq on 2011-01-21
ok now i can use /home/$USER/.public_html
but i am working on a html5 audio player and i wanted to have it use my music folder 
/home/$USER/.public_html/Music points to /home/$USER/Music
i am getting an error with the link
edit it is using the wrong location

---

### Post by pqwoerituytrueiwoq on 2011-01-21
i even tryed adding www-data to the root group it still cant see anything inside the home folder
how do i take it out of the root group?

---

