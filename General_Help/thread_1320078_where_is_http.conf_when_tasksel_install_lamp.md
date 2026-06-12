---
title: "where is http.conf when tasksel install lamp"
date: 2009-11-08
forum: General Help
---

### Post by iamgzy on 2009-11-08
Hi, masters

I just install lamp-server with tasksel, but the http.conf under etc/apache2 is 0 bytes. So would you please tell me where is the authentic http.conf to change the root path? or any config web page I can do the same as in WAMP?

many many thanks

---

### Post by dvlchd3 on 2009-11-08
I believe everything is configured through the apache2.conf file, and through virtual sites.  (sites-enabled directory)

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

---

### Post by iamgzy on 2009-11-08
> **dvlchd3 said:**
> I believe everything is configured through the apache2.conf file, and through virtual sites.  (sites-enabled directory)

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)


Thanks for quick reply ! Does help a lot.

Moreover, I find one line in the apache2.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

so does that mean i can overwrite the config in http.conf? Like in  login.conf for Shell?

---

### Post by Kareeser on 2009-11-08
Correct. Values in httpd.conf are for user-modified settings, if you don't feel like overwriting the default values in apache2.conf.

---

### Post by iamgzy on 2009-11-08
> **Kareeser said:**
> Correct. Values in httpd.conf are for user-modified settings, if you don't feel like overwriting the default values in apache2.conf.

Superb! Thank you !

---

