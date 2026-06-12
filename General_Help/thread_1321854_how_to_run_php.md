---
title: "how to run php"
date: 2009-11-10
forum: General Help
---

### Post by malikge on 2009-11-10
Hello...
I am new to linux. I am using ubuntu 8.10 and I have successfully installed LAMP(Apache and php) form the following site:

                 [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

but I don't know how to run php on linux. I remember how to run it on windows but don't know how to run it on linux. Can anyone help me by telling it in detail...
Thanks

---

### Post by nemiux on 2009-11-10
Go to the place its installed. There is a folder htdocs. Put files into it ( I mean php files, asd.php etc.) and go to [http://localhost/asd.php](http://localhost/asd.php) after started the server.

---

### Post by malikge on 2009-11-10
> **nemiux said:**
> Go to the place its installed. There is a folder htdocs. Put files into it ( I mean php files, asd.php etc.) and go to [http://localhost/asd.php](http://localhost/asd.php) after started the server.

Thanks for your replay... I told you that I am new to linux. I don't know where it is installed??? I have just followed the site and installed it. I don't know where it is. Can you plz help me on that too.
Thanks.

---

### Post by piratebill on 2009-11-10
You didn't really install lamp then (Linux Apache Mysql Php).  This is what I did
```
sudo tasksel
```

Check LAMP.

reboot and you should be good to go.

---

### Post by malikge on 2009-11-11
I have installed LAMP, and find a way to run php through it.
But I think that Nemiux have been mistaken, because htdocs is on windows and in linux the same thing is done in /var/www directory. There is no htdocs in linux...

---

### Post by fragos on 2009-11-11
When you installed LAMP PHP was installed but you need to configure apache to allow php execution. Go to /etc/apache2 and see if there is an httpd.conf file. Create it or add to it the following 3 lines:

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

Just a further note. PHP only run in a server which means that localy you'll need to point your browser to "localhost" and the PHP code will need to be in the /var/www folder so the browser can see it and execute as any other web page.

---

### Post by Bobulous on 2010-01-03
Just in case you intend to use PHP as a CGI executable rather than an Apache module, I've written a guide with the steps involved for Ubuntu:

[http://www.bobulous.org.uk/coding/apache-php-cgi.html](http://www.bobulous.org.uk/coding/apache-php-cgi.html)

Even with my poor memory, this lets me rebuild and reconfigure the whole setup in about half an hour, whereas it takes me hours if I'm hunting around the documentation looking for all the pieces.

---

