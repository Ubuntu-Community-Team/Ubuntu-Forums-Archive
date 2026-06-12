---
title: "Problems opening php files via localhost"
date: 2006-03-16
forum: General Help
---

### Post by dan4444 on 2006-03-16
Ok, so I finally was able to get the apache2 service started successfully again. Oddly enough, the httpd file left over from a previous not completely successful lampp installation (in my /opt/lampp/bin directory) was the location I ended up starting up apache2 successfully from.

Now I am having problems opening .php files in firefox via [http://localhost](http://localhost)
When I try [http://localhost/helloyo.php](http://localhost/helloyo.php), I get successive blank firefox windows being opened and it seems that if I did not stop it, they would go on forever. The contents of my helloyo.php file are:

<html>
<body>

<?php echo "Hello Yo!"; ?>

</body>
</html>


Anyone know what could be going wrong here? 

Thanks in advance.

Dan

---

### Post by JustRandomName on 2006-03-16
It appears you didn't use apt-get to install apache/php ... if you had things would have been much easier.

The reason firefox is trying to download the files is that you need to tell apache to process the .php files.

To do this you need something like this in your httpd.conf or apache2.conf files (depending on your version of apache).

```
AddType application/x-httpd-php .ph
```

---

