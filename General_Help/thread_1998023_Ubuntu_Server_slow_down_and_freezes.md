---
title: "Ubuntu Server slow down and freezes"
date: 2012-06-06
forum: General Help
---

### Post by LorenzoProdon on 2012-06-06
Hi,
i have a big problem:

Ubuntu Server 10.04 without reason slow down and freezes.
When is it  in freeze i can ping it, but with a big latency, but i can't connect ftp shh and can't load a webpages.

On this server i have installed wordpress and prestashop.

I want understand what is the problem that causes the freeze of this webserver:

From apache2 error.log i see in the moment of the freeze this error:

```
[Tue Jun 05 16:28:07 2012] [error] [client 89.121.253.227] client sent HTTP/1.1 request without hostname (see RFC2616 section 14.23): /w00tw00t.at.ISC.SANS.DFind:)
[Tue Jun 05 16:51:46 2012] [error] [client 180.76.6.233] PHP Warning:  mysql_connect(): Lost connection to MySQL server at 'reading authorization packet', system error: 104 in /var/www/store/classes/MySQL.php on line 34
[Tue Jun 05 16:59:34 2012] [error] [client 66.249.71.238] PHP Warning:  mysql_connect(): Lost connection to MySQL server at 'sending authentication information', system error: 32 in /var/www/store/classes/MySQL.php on line 34
[Tue Jun 05 17:04:31 2012] [error] [client 66.249.71.238] PHP Warning:  mysql_connect(): Lost connection to MySQL server at 'sending authentication information', system error: 32 in /var/www/store/classes/MySQL.php on line 34
```




Sorry for the bad english :)

---

### Post by LorenzoProdon on 2012-06-12
The server is freeze again, this is today apache2 log:

```
[Tue Jun 12 10:54:22 2012] [error] [client 95.227.123.170] File does not exist: /var/www/kasco1/favicon.ico
[Tue Jun 12 11:36:53 2012] [error] [client 220.181.108.91] PHP Warning:  mysql_connect(): Lost connection to MySQL server at 'sending authentication information', system error: 32 in /var/www/store/classes/MySQL.php on line 34
[Tue Jun 12 11:38:20 2012] [error] [client 178.208.98.128] PHP Warning:  mysql_connect(): Lost connection to MySQL server at 'reading authorization packet', system error: 0 in /var/www/store/classes/MySQL.php on line 34, referer: http://www.google.de/url?sa=t&rct=j&q=53049700049%20chra&source=web&cd=1&ved=0CGMQFjAA&url=http%3A%2F%2Fstore.turbo.it%2Fturbocharger%2F907-turbo-kkk-53049700049.html&ei=Aw3XT-juFYn-4QS337T1Ag&usg=AFQjCNGIngTT-EnJU7Tkrr3AasPl4D4xeg
```

:( Lost connection to MySQL server.
Nobody knows how to help me?

---

