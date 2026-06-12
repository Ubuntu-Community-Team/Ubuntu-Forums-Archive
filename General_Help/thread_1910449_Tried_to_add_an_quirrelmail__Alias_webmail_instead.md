---
title: "Tried to add an quirrelmail  Alias /webmail instead of /squirrelmail !!!"
date: 2012-01-17
forum: General Help
---

### Post by dchen on 2012-01-17
Hello all,

I was trying to add an Squirrelmail Alias /webmail for invoking the Squirrelmail webmail instead of /squirrelmail, but NOT successful, however, if my URL is: [http://localhost/webmail/](http://localhost/webmail/)  (with "/" at the end) it works!
The URL [http://localhost/webmail](http://localhost/webmail) (without the "/" at the end) WON'T work !!! any thought ?

I add a line below in the /etc/squirrelmail/apache.conf file

Alias /webmail  /usr/share/squirrelmail

Ran under Ubuntu server 11.10.

---

### Post by dchen on 2012-01-18
Hi all,

The following forms of URL to access SquirrelMail work with Login screen !

   [http://127.0.0.1/webmail](http://127.0.0.1/webmail)
   [http://192.168.0.108/webmail](http://192.168.0.108/webmail)        (The Ubuntu server IP address)
   [http://localhost/webmail/](http://localhost/webmail/)
   [http://localhost/squirrelmail](http://localhost/squirrelmail)

However, [http://localhost/webmail](http://localhost/webmail)   NOT WORKING !!  the Firefox browser just NO RESPONSE at all !!

I have the line in the /etc/hosts file:
127.0.0.1   	localhost

Anyone explains why ?

---

