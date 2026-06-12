---
title: "Someone hacked me?"
date: 2010-06-10
forum: General Help
---

### Post by Nonno Bassotto on 2010-06-10
I use to keep a running instance of Apache in order to test my sites locally. I'm usually not that fussy about security, assuming my 80 and 8080 ports are closed (and, well, also the other ones).

Anyway this evening I was just logging into PHPMyAdmin when I found the default username was a string of garbled characters. When I entered PHPMyAdmin, I was greeted with the message
```

Additional features have been disabled in order to work with linked tables. To find out why click here.

```

So I clicked and it seems that the error comes from the table
```
$cfg['Servers'][$i]['tracking']
```
which has been disabled. Everything else SEEMS ok at first sight.

So now I have got a few questions.
1) I checked via canyouseeme.org and the default ports are still closed. This mean it should be impossible to even try to do something on my Apache remotely, right?
2) How do I reenable the additional features?
3) How do I check if someone else logged in?
4) What about the garbled name at the login? This should be just a Firefox thing, or actually PHPMyAdmin does suggest the name of the latest login?
5) How do I set up Apache to serve only the computers in the LAN? At worst, even only the local computer would be good.

---

### Post by mechdave on 2010-06-10
To start with you need to close up apache. You need to find the site file in /etc/apache2/sites-enabled/ (usually 000-default) and open it with your favourite text editor. You need to add inside the <Directory /> tag the following
```

Order Deny,Allow
Deny from all
Allow from 127.0.0.1 #local host only, you can put in your lan ip address here too

```

This will stop all traffic to your apache except your machine (127.0.0.1) You can use use the ip address notation of xxx.xxx.xxx.xxx/xx to allow only lan traffic, you need to learn subnetting for that tho :)

To see who has been accessing your server you need to look at /var/log/apache2/access.log This will tell you usually the ip address and what they tried to access on your server. When I had my server running I had repeated attacks on it to try and use a php vunerability to forward spam from china!! If your server is wan facing you need security and daily (very important) checks on logs. I also upped the logging as well which gave me more details of who was connecting. to my machine :)

For more on apache settings see --> [http://httpd.apache.org/docs/2.2/howto/access.html](http://httpd.apache.org/docs/2.2/howto/access.html)

As for the database and phpMyAdmin I can't help you :)

Good luck

---

### Post by Nonno Bassotto on 2010-06-11
Thank you very much for your help! :-) Actually I have two more questions.

6) Apache (with a default configuration) will not accept connections on ports different from 80 and 8080, right?
7) The only unusual thing I have found on my logs is a bunch of entries like these:
```
::1 - - [08/Jun/2010:23:14:25 +0200] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
```
Are these OK? What do they mean?

---

### Post by mechdave on 2010-06-11
Have a read of this page, it should explain why you are seeing the internal dummy connection.  --> [http://wiki.apache.org/httpd/InternalDummyConnection](http://wiki.apache.org/httpd/InternalDummyConnection)

Google is your best friend when things like this happen :)

Apache with standard config will only accept connections on port 80, port 8080 is generally used for proxy access.
You can change the ports that apache listens to by changing the /etc/ports.conf file or by virtual host in your server config file (/etc/apache2/sites-enabled/*)
I suggest you read the docs here --> [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)
This documentation is comprehensive and well worth a good read through so you can understand exactly what you are doing eith configuration of your server :)

---

### Post by Nonno Bassotto on 2010-06-12
Thank you very much for your help.

---

