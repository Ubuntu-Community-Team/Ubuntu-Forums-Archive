---
title: "Simple Image Crawler for Linux?"
date: 2009-08-27
forum: General Help
---

### Post by paradigm2 on 2009-08-27
Hello I am looking for something which will scan a domain for images and download them.  I tried mnogosearch but the thing is ridiculous in complexity and the configuration seems poorly documented as far as being usable.

---

### Post by paradigm2 on 2009-08-27
bump

---

### Post by Johnny B on 2009-08-27
how about a firefox addon?
[https://addons.mozilla.org/en-US/firefox/addon/201]("https://addons.mozilla.org/en-US/firefox/addon/201")

---

### Post by paradigm2 on 2009-08-27
> **Johnny B said:**
> how about a firefox addon?
[https://addons.mozilla.org/en-US/firefox/addon/201]("https://addons.mozilla.org/en-US/firefox/addon/201")

It is a step in the right direction but I just want to be able to point it at a domain and have it crawl and then download all images.  I want it to do this on a regular basis automatically.

Mnogosearch would work if it actually worked but every step along the way has been a total pain because the documentation lacks any sort of guided basic tutorial. And while the docs cover things they don't explain things fully or provide near enough examples so for each and every little thing there exists ambiguity enough such that there are dozens of different options.

---

### Post by paradigm2 on 2009-08-31
I retract the negative comments about mnogosearch. It is difficult to master initially but once you do it is very useful. I was simply frustrated. Reading the web board there is a MUST if you are trying to figure it out!

---

### Post by larytet on 2010-08-04
Short HowTo for mnogosearch. This HowTo based on [http://www.mnogosearch.org/board/message.php?id=19573](http://www.mnogosearch.org/board/message.php?id=19573)

I assume that apache2, mysql, phpmyadmin present. I am using Ubuntu 10.04. This HowTo is not very detailed, but more general guide for advanced user.

You need first install compiler, mysql, text conversion utilities, development packages for mySQL and ZLIB
```

sudo aptitude -o Acquire::http::Proxy=http://<proxy>:80 install build-essential zlib1g-dev libmysqld-pic  mysql-common mysql-server mysql-client phpmyadmin
sudo aptitude -o Acquire::http::Proxy=http://<proxy>:80 install catdoc poppler-utils  ppthtml

```

Download and open tar with mnogosearch source code.

From the source directory
```

./install.pl
make
sudo make install

```
Likely you are going to need install buildessential libsqlclient-dev packages and may be some others.

In the file /usr/local/mnogosearch/etc/indexer.conf fix line 
```

DBAddr  mysql://root:password@localhost/mnogosearch/?dbmode=blob

```
I assume name of the mySql data base mnogosearch

Configure proxy, disable file extensions like *.o, *.nb0, etc.
Add servers to crawl 
Get over all other things and change if needed

Create data base mnogosearch using [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Take care of configuration files
```

sudo cp etc/search.htm-dist etc/search.htm
sudo cp etc/stopwords.conf-dist etc/stopwords.conf
sudo cp etc/langmap.conf-dist etc/langmap.conf

```

Fix data base access in the file etc/search.htm similar to the line above with DBAddr
Create SQL table in the database mnogosearch and run indexer
```

cd /usr/local/mnogosearch
sbin/indexer  -C
sbin/indexer  -Ecreate
sbin/indexer

```

Copy search.cgi to /usr/lib/cgi-bin/. (see also file /etc/apache2/sites-available/default for alias /cgi-bin/)

This link should work [http://localhost/cgi-bin/search.cgi](http://localhost/cgi-bin/search.cgi)

---

