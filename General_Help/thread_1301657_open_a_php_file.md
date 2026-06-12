---
title: "open a php file"
date: 2009-10-26
forum: General Help
---

### Post by mamali on 2009-10-26
I start to learn php and just wondering how to process .php files with firefox. Every time I link to a file with .php, it asks me to save or open with a text editor. ( I have PHP, mySQL and Apache installed)
Thanks.

---

### Post by mikejonesey on 2009-10-26
to process php localy you will need to install a couple of things.

1. php
2. apache (this will enable you to browse local php it's a web server)
3. webmin (optional, but will make your life alot easyer, it enables you to add hosts n stuff)
4. mysql (optional but if your php requires a db you will want this)

all are avalible via your synaptic package manger.

once installed you can goto [http://localhost](http://localhost) to view your local files in firefox

to use webmin to define which floder localhost will read go to webmin:
[http://localhost:10000](http://localhost:10000)

go to servers->apache->global config->config files

and select /etc/apache2/sites-avalible/default

and edit the document root

you may have to use chmod or nautilus to edit file permisions.

---

### Post by martrn on 2009-10-26
> **mamali said:**
> I start to learn php and just wondering how to process .php files with firefox. Every time I link to a file with .php, it asks me to save or open with a text editor. ( I have PHP, mySQL and Apache installed)Thanks.

Ensure you install the modification to apache ```
sudo apt-get install php5 libapache2-mod-php5
```. You need to put your php files at directory /var/www/  and make directory /var/www/  read/writable/executable, ```
sudo chmod -R 777 /var/www
```   --or-- edit your apache config file.  ```
sudo gedit /etc/apache2/apache2.conf
```.  Then restart apache (on latest version is: )```
 sudo /usr/sbin/apache2ctl restart
```

---

### Post by Giblet5 on 2009-10-26
You'll wanna install all of that stuff via ```
sudo apt-get install mysql-server-5.1 mysql-client-5.1 apache2 php5 php5-cli phpmyadmin
```

The text editor "kate" is quite good for PHP coding.

---

### Post by martrn on 2009-10-26
Gphpedit is good as a php text editor, finds the correct files, and good php highlighting and syntax options.

```
sudo apt-get install gphpedit
```

---

### Post by Giblet5 on 2009-10-26
> **martrn said:**
> Gphpedit is good as a php text editor, finds the correct files, and good php highlighting and syntax options.

```
sudo apt-get install gphpedit
```

Sweet! I hadn't tried that one...until now.

I suspect the use of kate is ingrained now... Must. Fight. Urge.

---

