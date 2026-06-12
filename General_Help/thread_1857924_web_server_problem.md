---
title: "web server problem"
date: 2011-10-11
forum: General Help
---

### Post by nikhidet on 2011-10-11
hey all,
i need helps from those Linux experts here....my laptop currently running ubuntu 10.04 Lts.Actually im such a nob but i am interested in creating web server.somehow i have managed to create apache and it is working well.i also somehow managed to use shell cgi script on this apache..but now come a problem...i want to authenticate my server but i still dont have any idea on how to do that...i read something on Internet it and it stated about my httpd.conf. but for my httpd.conf,there is nothing inside this file...hopefully someone can help me..thanks in advanced

---

### Post by mikejonesey on 2011-10-11
authenticate it? do you mean you would like to test drive ssl on it? or do you mean a http authentication? (htpass)

---

### Post by jazzon on 2011-10-11
By authenticat do you mean [HTTPS://,](HTTPS://,) or simply a password login of some kind (lots of ways for password), HTTPS is done with SSL certificates, (not too hard).

httpd.conf is the file used by apache versions below 2 to configure themselves.

With ubuntu the file your looking for is /etc/apache2/apache2.conf. more config files are found in /etc/apache2/conf.d/.  THese get read into apache2.conf at startup time for apache.

If you are talking about conf directives that will be specific for your site , write a separate mysite.conf file and put it in /etc/apache2/sites-available .File should be named <your site name goes here> with no extension. Then activate the site by:
```
sudo a2ensite <sitename goes here>
```
Then restart apache2
```
sudo service apache2 restart
```

---

### Post by SeijiSensei on 2011-10-11
[http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html)

---

