---
title: "Duplicated vhost"
date: 2009-11-25
forum: General Help
---

### Post by evayroberto on 2009-11-25
Hi. Maybe its a stupid easy problem. I have ubuntu server 9.04, I create one virtualhost and I cant access to it via web browser..when I check apache error log, I can see that apache is searching in a duplicated content
ex: vhost directory and document root is set to /var/www/example.com
and error log shows that the apache search is in /var/www/example.com/example.com ..., so, site is not reachable.
And if i create a simple php file and I put into /var/www/example.com, If I want to see it i must type [http://server.ip/simple.php](http://server.ip/simple.php)...
Why???? thanks

---

### Post by evayroberto on 2009-11-25
please, any help???

---

### Post by evayroberto on 2009-11-26
Problem persists....

---

### Post by mbeach on 2009-11-26
> **evayroberto said:**
> I create one virtualhost and I cant access to it via web browser

can you post the output of:
```
grep -i -e virtualhost -e ServerName -e documentroot /etc/apache2/sites-enabled/* 
```

---

